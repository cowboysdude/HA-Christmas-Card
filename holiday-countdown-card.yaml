# Holiday Countdown Card for Home Assistant
# Counts down to Christmas, shows MERRY CHRISTMAS on Dec 25,
# counts down to New Year's from Dec 26, shows HAPPY NEW YEAR on Jan 1,
# then starts counting down to Christmas again.
# Requires christmas-tree.svg and new-year.svg in /config/www/ (see README.md).

type: markdown
content: |
  {% set t = now().date() %}
  {% if t.month == 12 and t.day == 25 %}{% set mode = 'xmas_day' %}{% set target = t %}
  {% elif t.month == 1 and t.day == 1 %}{% set mode = 'ny_day' %}{% set target = t %}
  {% elif t.month == 12 and t.day > 25 %}{% set mode = 'ny' %}{% set target = t.replace(year=t.year + 1, month=1, day=1) %}
  {% else %}{% set mode = 'xmas' %}{% set target = t.replace(month=12, day=25) %}{% endif %}
  <center>

  {% if mode == 'xmas_day' %}
  <img src="/local/christmas-tree.svg?v=1" width="100">

  <font size="7"><b>MERRY CHRISTMAS!</b></font>

  {% elif mode == 'ny_day' %}
  <img src="/local/new-year.svg?v=1" width="140">

  <font size="7"><b>HAPPY NEW YEAR!</b></font>

  {% else %}
  {% set d = (target - t).days %}
  {% if mode == 'xmas' %}<img src="/local/christmas-tree.svg?v=1" width="100">{% else %}<img src="/local/new-year.svg?v=1" width="140">{% endif %}

  <font size="7"><b>{{ d }}</b></font>

  ### {{ 'day' if d == 1 else 'days' }} until {{ 'Christmas' if mode == 'xmas' else "New Year's" }}

  <font color="gray">{{ target.strftime('%A, %B %-d, %Y') }}</font>
  {% endif %}

  </center>
