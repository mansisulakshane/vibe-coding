

Readme · MD
🧵 SutRa — Every Choice Weaves a New Story
SutRa is an interactive storytelling platform. Authors build branching, choose-your-own-adventure stories with a visual story map, and readers play them as a sequence of illustrated flash cards, discovering different endings along the way.

It is a single-file web app (index.html) with no build step, no dependencies, and no backend. Everything runs in the browser and saves to localStorage.

✨ Features
Reading
Each scene appears as a popup flash card with an animated gradient border (gold for endings).
Animated hover effects on choice buttons (slide, glow, shine).
Optional typewriter effect (click the text to skip it).
Progress bar, inventory display, Restart, and Return to library.
Ending collection: discovered endings persist across restarts.
Locked choices (🔑) that appear only after you collect an item.
Respects the browser's reduced-motion setting.
Authoring
Scene editor: title, text, scene type (Normal / Start / Ending), up to 4 choices per scene.
Visual story map: draggable nodes, animated flowing connections, a pulsing start node, dashed gold ending nodes, and a legend.
Hover a node to trace its paths.
Link mode to connect scenes by clicking source then target.
Zoom, fit-to-screen, and scene search.
Story variables (true/false) with a "requires" condition and a "sets true" action on each choice. No eval is used.
Undo / redo (bounded to 60 steps per session) and an activity log.
Photos: generated cinematic artwork for every cover and scene, plus upload of your own cover or scene photos (resized and stored as JPEG data).
Roadmap view 🗺: a level-by-level map of the story ("Jump 1…6"), showing where each choice leads, which endings are found, and which scenes are dead ends or unreachable.
Safe scene deletion
Deleting a scene shows calculated impact (incoming and outgoing choices, newly unreachable scenes, new dead ends, reachable endings before and after). You pick one of three strategies:

Strategy	What it does
A · Remove	Deletes the scene and all its connections.
B · Redirect	Lets you choose a new destination (and reword the choice) for each incoming link.
C · Bridge	Moves incoming links to a target scene, adds a short editable "key details" line to it, drops decorative text, and carries over outgoing choices that fit under the four-choice limit.
Deleting the start scene requires choosing a replacement. After deletion, Undo restores the original scene and links.

Warnings and validation
Story Health tab detects: missing start, empty titles, broken links, more than 4 choices, unknown variables, dead ends, unreachable scenes and endings, and endings with outgoing choices.
A banner on the map shows error and warning counts, and clicking it jumps to the problem scene. Dead-end nodes pulse red.
Library cards show a warning tag when a story has problems.
If a reader reaches a dead end, they get a clear message with Restart and Return options.
Validation is structural. It cannot tell whether a story still makes sense after edits, so review changed scenes yourself.

Library
Search and filter by length (Short / Medium / Long).
Random Adventure.
JSON export and validated import (checks syntax, scene IDs, start scene, destinations, scene types, and the 4-choice limit before anything is added).
Light and dark themes.
Included stories
Story	Length	Notes
The Lantern Fox	Short	5 scenes, 2 endings
The Midnight House: Choose Your Fear	Medium	13 scenes, 4 endings, hasKey secret route
The Lighthouse at the Edge of Dreams	Medium	14 scenes, every path has exactly 6 choices, secret ending via moonPearl
Starbound Relay	Long	16 scenes, 4 endings, hasCore variable
🚀 Getting started
No installation is needed.

bash
git clone https://github.com/<your-username>/sutra.git
cd sutra
# open index.html in any modern browser
Or serve it locally:

bash
npx serve .
# or
python3 -m http.server 8000
Deploy for free
GitHub Pages: push index.html, then go to Settings → Pages and choose the branch and root folder.
Netlify / Vercel / Cloudflare Pages: drag and drop the folder.
Rename sutra.html to index.html before deploying.

🕹 How to use
Play: on the library page, click ▶ Play on a story.
Create: click ✍ Create Your Story, then open the editor.
Edit: pick a scene in the left list or on the map, then edit it in the right panel.
Connect: change a choice's destination, or use 🔗 Link mode on the map.
Check: open the Health tab, or click 🗺 for the roadmap.
Share: use ⬇ on a story card to download its JSON file. Others can load it with ⬆ Import JSON.
📦 JSON format
json
{
  "schema": 1,
  "story": {
    "id": "…", "title": "…", "desc": "…", "genre": "…", "len": "Short|Medium|Long",
    "vars": ["hasKey"],
    "start": "s1",
    "scenes": {
      "s1": {
        "id": "s1", "t": "Title", "text": "Scene text…", "type": "s|n|e",
        "px": 30, "py": 20,
        "ch": [{ "t": "Choice text", "to": "s2", "req": "hasKey", "set": "" }]
      }
    }
  }
}
🗂 Data and privacy
All data lives in your browser's localStorage (key sutra.v1). Clearing site data deletes your stories, so export anything important.
Nothing is sent to any server. No accounts, analytics, or API keys.
Story text is HTML-escaped before rendering, and imported JSON is validated before use.
Browser storage is limited (roughly 5 MB), so many large uploaded photos can fill it. The header shows "Save failed" if that happens.
⚠️ Current limitations
This version is local-first. These items from the original product spec are not implemented yet:

PostgreSQL / Supabase backend, accounts, and server-side authorization
Publishing, shareable public links, ratings, reviews, and reports
Persistent version-history snapshots and "restore version" (only session undo/redo and an activity log exist)
Rich-text editing (TipTap), scene icons, and conditions beyond true/false variables
Number and text variables, and "replace existing story" on import
AI writing assistant
Achievements, daily challenge, English/Hindi language switch
Reading statistics and charts
Real photographs: the artwork is procedurally generated SVG, so use the upload feature for photos
🛣 Roadmap
 Supabase (PostgreSQL, Auth, Storage) with Row Level Security
 Server-side enforcement of the 4-choice limit
 Version history with restore
 Public sharing and reviews
 TipTap rich-text editor and number variables
 Optional AI assistant through a secure backend
 Achievements and reading statistics
 Hindi localization
🧰 Tech
Vanilla HTML, CSS, and JavaScript. Inline SVG for the story map and artwork. localStorage for persistence. No frameworks or CDN dependencies.

🤝 Contributing
Issues and pull requests are welcome. Please keep the app dependency-free and make sure the Story Health checker still passes on all bundled stories.

📄 License
MIT. Add a LICENSE file before publishing.

The bundled stories and generated artwork are original to this project.


Claude finished the response
