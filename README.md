🎄 Holiday Countdown Card 🥂

An animated Christmas and New Year's countdown card for Home Assistant. It uses only the built-in Markdown card, so you don't need HACS or any custom cards.

Show Image Show Image Show Image

Animated preview of the Holiday Countdown Card

The card counts down to Christmas with a twinkling tree, celebrates on the day, then switches to a champagne-and-confetti countdown to New Year's. Then it starts over for next year. Once it's set up, you never have to touch it again.

✨ Features
Changes on its own through the season. It knows which holiday is next and switches between them by itself.
Animated artwork.
🎄 Christmas tree: the tree sways, the lights twinkle, the star glows and snowflakes fall.
🥂 New Year's: champagne flutes clink with a sparkle, bubbles rise, streamers sway and confetti falls.
Works with any setup. It's a plain markdown card using Home Assistant templates, so there's nothing to install from HACS.
Lightweight. The two SVG files add up to about 13 KB. The animations use plain SVG/CSS with no JavaScript.
Repeats every year. The year rolls over automatically.
📅 What it shows

All four card states

Date	Artwork	Text
Jan 2 – Dec 24	🎄 Christmas tree	X days until Christmas
Dec 25	🎄 Christmas tree	MERRY CHRISTMAS!
Dec 26 – Dec 31	🥂 Champagne & confetti	X days until New Year's
Jan 1	🥂 Champagne & confetti	HAPPY NEW YEAR!

On the last day of a countdown, "days" becomes "day".

📦 Installation
1. Add the images

Download both SVG files from the www/ folder:

christmas-tree.svg
new-year.svg

Copy them into your Home Assistant /config/www/ folder. Any of these will do:

the File editor add-on (use its upload button)
the Studio Code Server add-on (drag and drop)
the Samba share add-on (copy them over the network)

[!NOTE] If the www folder didn't exist before, create it and restart Home Assistant once. Files in /config/www/ are served at /local/.

To check that it worked, open http://<your-home-assistant>:8123/local/christmas-tree.svg in a browser. You should see the animated tree.

2. Add the card
Dashboards edited in the UI (most people)
Open your dashboard and click ✏️ Edit dashboard.
Click + Add card and choose Manual at the bottom of the list.
Replace everything in the editor with the contents of holiday-countdown-card.yaml.
Click Save.
YAML-mode dashboards (ui-lovelace.yaml)

Paste the card under any view's cards: list. Indent it so - type: markdown lines up with your other cards:

yaml
views:
  - title: Home
    cards:
      - type: markdown
        content: |
          {% set t = now().date() %}
          ...

Save the file and refresh your browser. YAML dashboards don't need a restart.

🎨 Customizing
Change	How
Image size	Edit width="100" (tree) or width="140" (champagne) in the card
Text size	<font size="7"> is the largest. Try 5 or 6 for a smaller card
Images don't change after you edit the SVGs	Change ?v=1 to ?v=2 in the card so browsers fetch the new files
Different colors	Open the SVGs in any text editor. Colors are standard hex codes like 
#ff4d4d
Preview any date

To see what the card will show on a given day without waiting:

Go to Developer Tools → Template.
Paste the card's content (everything under content: |).
Replace now().date() with as_datetime('2026-12-25').date(), using whatever date you want to test.

The preview on the right updates as you type.

❓ Troubleshooting
Problem	Fix
Broken-image icon instead of the artwork	The SVGs aren't in /config/www/. Check the path, and restart Home Assistant if you just created the www folder
The artwork shows but doesn't move	Some browsers pause animations when the tab is in the background. Switch to the tab and they'll start again
The count is off by a day	Check that your time zone is correct in Settings → System → General
Text is too big on phones	Lower <font size="7"> to 5 or 6
📁 Repository contents
├── holiday-countdown-card.yaml   # The card (paste into the Manual card editor)
├── www/
│   ├── christmas-tree.svg        # Animated Christmas tree
│   └── new-year.svg              # Animated champagne, streamers & confetti
└── images/
    ├── tree.png                  # Logo / icon
    ├── preview.gif               # Animated preview
    └── all-states.png            # All four card states
🤝 Contributing

Ideas for more holidays (Halloween, Thanksgiving, birthdays and so on), new artwork or fixes are welcome. Open an issue or a pull request.

📄 License

Released under the MIT License. You're free to use, change and share it.
