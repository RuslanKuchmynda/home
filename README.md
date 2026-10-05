# home

A personal start page for the browser. Clock, search, grouped links, world clock, weather — zero dependencies, one file.

## Run

No build step. Just open it:

**Option 1 — open the file directly**

Open `index.html` in Chrome. Everything works except it can't be set as the
new-tab page this way (Chrome restriction).

**Option 2 — local server (recommended)**

```bash
cd home
python3 -m http.server 8901
```

Then open http://localhost:8901. Keep the terminal open while you browse.
To auto-start on macOS login:

```bash
# adjust the path, then load it once
launchctl load ~/Library/LaunchAgents/home.page.plist
```

with `~/Library/LaunchAgents/home.page.plist`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<plist version="1.0">
<dict>
  <key>Label</key><string>home.page</string>
  <key>ProgramArguments</key>
  <array>
    <string>/usr/bin/python3</string>
    <string>-m</string>
    <string>http.server</string>
    <string>8901</string>
  </array>
  <key>WorkingDirectory</key><string>/path/to/home</string>
  <key>RunAtLoad</key><true/>
  <key>KeepAlive</key><true/>
</dict>
</plist>
```

**Use it as the new-tab page**

1. Install the [New Tab Redirect](https://chromewebstore.google.com) extension.
2. Extension options → Redirect URL → `http://localhost:8901`
   (or `file:///path/to/home/index.html` — then also enable
   *Allow access to file URLs* in `chrome://extensions` → Details).
3. Set it as homepage / startup page in Chrome settings if you like.

## Features

- Big clock, date, Google search (`/` focuses it)
- Link groups with per-group add button; right-click or ✎ to edit
- Keyboard: `1`–`9` opens a link in a new tab
- Second world clock (GMT offsets, hideable) + weather (Open-Meteo, keyless)
- Everything stored in the browser's `localStorage` — no backend, no tracking
