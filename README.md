# Personal Network Map

An interactive map of the people in your life, built to solve one problem: remembering who you know, where they are, and when you last spoke. It is a single self contained HTML file. No server, no build step, no tracking. You open it, enter a passcode, and explore your network three ways.

Live example: https://halisy.github.io/pn/ (passcode protected)

## What it does

Your network is drawn as a tree that starts at you and branches into spheres (the circles of life you know people through, like a lab, a university, a volunteering group) and then into people. From there you can look at the same network in whatever way is useful in the moment.

**Three views**, switched from the toggle at the top left:

- **By sphere** shows the tree rooted at you, branching into your spheres and then the people in each. This is the mental model of how you actually know people.
- **By city** regroups everyone by the place they live. Open a city before a trip and you see everyone you know there, sorted by who is most worth reaching out to.
- **World map** places a pin on every city where you know someone, sized by how many people are there. Scroll to zoom into busy regions. Click a pin to see who is there.

**Reconnect radar** is a side panel that ranks people by how important they are to you and how long it has been since you last spoke, so the ones going cold rise to the top. One click logs that you reached out today.

**Friends of friends** are supported. When you add someone, you can say who introduced you, and the line is drawn from that friend to them rather than from you. This keeps second degree contacts honest.

**Multiple cities per person** are supported. Someone who splits time between two places shows up under both.

**Search** filters by name, role, city, or tag across every view.

## How to use it day to day

1. Open the page and enter the passcode.
2. Click **+ Person** to add someone. Fill in their name, sphere, one or more cities (comma separated), how you know them, a relevance score from 1 to 5, and optionally who introduced you.
3. Click any person to see their details. Use **Contacted today** to reset their reconnect timer.
4. Switch to **World map** or **By city** when you want the geographic picture, for example before travelling.
5. If a small town does not place itself on the map, it appears in a short list at the bottom. Click the town, then click the map to drop its pin. It is remembered after that.

## Make it your own

This map ships with one person's data, but it is meant to be copied and refilled with your own.

1. **Fork or download** this repository.
2. **Change the passcode.** Open the map, click the `...` menu, type a new passcode under "Change your passcode," and click Generate hash. Copy the hash it gives you and paste it as the value of `PASS_HASH` near the top of `index.html`. This way your passcode is never written in the file in plain text.
3. **Clear the example people and add your own.** The simplest path is to open the map, delete the sample people, and add yours through the **+ Person** button. Your entries are saved in your browser automatically.
4. **Make your data permanent.** Browser storage is per device. To bake your people into the file so every device shows them, open the `...` menu, click **Copy data block for GitHub**, and paste it over the `SEED_DATA` block in `index.html`. Or click **Download data (JSON)** to keep a backup, and **Import data** to load it back.

## Hosting your own copy on GitHub Pages

1. Put `index.html` and the empty `.nojekyll` file in a repository.
2. In the repository, open **Settings**, then **Pages**.
3. Under Branch choose `main` and folder `/ (root)`, then Save.
4. Wait about a minute. Your map is live at `https://<your-username>.github.io/<repo-name>/`.

To update it later, edit `index.html` (or paste in a fresh data block) and push again.

## Data and privacy, honestly

- Everything lives inside the single HTML file and your browser. There is no backend and nothing is sent anywhere.
- The passcode only hides the interface. It is client side, so anyone who opens the page source can read past it. A public GitHub repository also means the file, and everyone in it, is readable by anyone who finds it.
- If your network is sensitive, keep the repository private and open the file locally by double clicking it, or use a host that offers a real login. Do not rely on the passcode as security.

## Under the hood

- One HTML file with everything inlined: the [D3](https://d3js.org) library, country outlines, and a lookup of several thousand world cities, so the whole thing works offline.
- Country shapes come from [world-atlas](https://github.com/topojson/world-atlas). City coordinates come from an open cities dataset.
- No frameworks, no dependencies to install, no accounts.

## License

Use it, fork it, adapt it freely for personal use.
