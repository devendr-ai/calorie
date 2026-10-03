# Plate (standalone web app)

Plate is a photo calorie tracker tuned for vegetarian Indian food. This folder is the whole app: put it on any static host, open the link on your iPhone, and add it to your Home Screen.

## What you need
- A free static host (steps below).
- An Anthropic API key (console.anthropic.com, API keys). It is separate from a Claude subscription and bills per use. Set a monthly spend limit in the Console.

## 1. Host it (pick one)

**GitHub Pages**
1. Create a new public repository (any name).
2. Upload everything in this folder (index.html, sw.js, manifest.webmanifest and the three icon files) to the repository root.
3. Settings, Pages, Build from branch, main, / (root), Save.
4. After a minute the app is at https://YOUR-USERNAME.github.io/REPO-NAME/

**Cloudflare Pages**
1. Workers and Pages, Create, Pages, Upload assets.
2. Drag in this folder and deploy. You get https://NAME.pages.dev

Either way it is a five-minute job from a laptop. Both are free.

There are no keys or secrets in these files, so a public repository is fine. Your API key is typed into the app on your phone and stays there.

## 2. Install on iPhone
1. Open the link in Safari.
2. Share, Add to Home Screen, Add.
3. Open Plate from the Home Screen icon and do all setup there. iOS gives a Home Screen app its own storage, separate from Safari, so a key entered in Safari will not be there. Home Screen apps are also exempt from Safari's 7-day clearing of website data.

## 3. First run
1. Settings: paste your API key and tap Save and test.
2. Settings, Your kitchen: katori size, roti size, how much oil or ghee you use.
3. Snap a meal.

## Cost
Roughly 2 to 4 cents per photo on Standard (Claude Sonnet 5.5) and several times that with Max accuracy (Claude Opus 5.5). These are estimates from published token prices. Check Console, Usage after a few days.

## Your data
- Stored on this device only (IndexedDB). No server, no sync.
- Settings, Back up data creates a .json file (share sheet, Save to Files). Restore backup loads it. Back up before you delete the app icon, change phones, or clear Safari data.
- Your API key is never included in a backup.

## Updating
Replace the files on your host with the new copy. Then swipe the app away completely and open it again while online. iOS can keep showing the old version until you do.

## Troubleshooting
- "Anthropic could not process that request": the card shows Anthropic's exact reason underneath it. The usual causes are an account with no credit yet (Console, Billing), a spend limit that has been reached (Console, Limits), or a key from a workspace without access. After fixing it, open Settings and tap Test key. It sends a tiny test photo and shows Anthropic's reason right there if something is still wrong.
- "Anthropic rejected that API key": paste it again (it starts with sk-ant-).
- "balance is empty": add credit in the Console.
- "model name was not found": Settings, Models, and enter a current model name from Anthropic's docs.
- "browser blocked on-device storage": you are in Private Browsing or storage is disabled. Use a normal tab or the Home Screen app.

## Limits
- No Apple Health integration (a web app cannot write to Health).
- No sync between devices.
- Photo estimates are typically 15 to 30 percent off. Ghee and oil are the biggest unknowns, which is why Your kitchen matters.
