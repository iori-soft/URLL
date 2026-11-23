# URLL (URLLauncher) v0.008

English | [日本語](README.ja.md)

**Open a URL in your browser with a single shortcut key.** URLL is a macOS menu bar app.

## Features

 - **URL Jump**: Pair a shortcut key with a URL, and the key opens that URL.
 - **App Launch**: A shortcut key launches an app you registered.
 - **Key Action**: A shortcut key sends a different key to the frontmost app.
  (Example: press ⌥W to send ⌘W (Close Tab) to the frontmost app.)

## Getting Started (Installation)

URLL is notarized by Apple.

1. Download the DMG from [the URLL website](https://iori-soft.github.io/), open it, and drag **URLL** into the Applications folder.
2. Open URLL. If macOS says the app was downloaded from the internet, click **Open**.
3. URLL starts and its icon appears in the menu bar.
4. Only if you use Key Actions: in Settings, open the "Key Actions" tab, click **Allow…**, and turn on URLL under **Accessibility** (see "Accessibility Permission" below).
   <!-- Screenshot: Accessibility permission (coming soon) -->

## Details

#### URL Jump
**Open a URL with ⌥ + a letter from any app**
   - Opening URLs and apps does not need Accessibility permission.
   - Nothing is registered on first launch, so the Settings window opens automatically.
   - To set or change a key, click the key button in Settings and press the key.

**Assign keys to the URLs you open often**
   - Add or delete sets of name, URL and key.
   - A key is a combination of ⌥, ⌘ or ⌃ with another key. The same key cannot be used on two rows. Keys already used by other apps or by macOS cannot be registered either.
   - A row without a key becomes a menu-only item. If you run out of keys, give keys only to the items you use most.
   - URL schemes such as `shortcuts://`, `mailto:` and `x-apple.systempreferences:` also work (they open the matching app).
   - A URL without a scheme (such as example.com) gets `https://` added automatically.

#### App Launch
**Register apps as well as URLs**
   - In the "Apps" tab of Settings, choose an app with "Add App…". The key then launches the app or brings it to the front (the field holds `/Applications/….app`).

#### Key Action
**Assign key actions too (such as Close Tab ⌘W)**
   - In the "Key Actions" tab of Settings, click "Add Key Action" and choose the key to send to the frontmost app when you press your shortcut.
   - From the list of common actions you can pick Close Tab (⌘W), Close Window (⇧⌘W), Reopen Closed Tab (⇧⌘T), Next/Previous Tab (⌃Tab / ⌃⇧Tab), Minimize Window (⌘M), Hide App (⌘H), Quit App (⌘Q) and more. You can also record any key with the "Send" key button.
   - Example: assign "Close Tab (⌘W)" to ⌥W, and pressing ⌥W in any app works like pressing ⌘W.
   - Sending keys needs **Accessibility permission** (see "Accessibility Permission" below).
   - If the key to send is the same as one of URLL's own shortcuts, it would repeat itself, so URLL stops this when you save or import.

#### Other Features
**Show your assigned shortcuts with ⌃/**
   - Press ⌃/ (default) in any app to show a "key → name and target" list in the middle of the screen. Changes to the settings show up right away.
   - Close it with ⌃/ again, Esc, or a click outside the panel. Click a row to open its URL or app.
   - The list appears without taking focus away from the app you are using. You can also open it with "Show Shortcut List" in the menu.
   - Change or remove the list key in the "General" tab of Settings.
**Export and import settings**
   - Back up and restore your settings as an easy-to-read **text file (.txt)**.
   - Use **Export Settings…** and **Import Settings…** in the menu bar menu (or the buttons at the bottom of Settings).
   - You can also open the file in a text editor to edit or add items (see "Settings Text File Format" below).
**Lives in the menu bar (not in the Dock)**
   - From the 🔗 icon at the top right of the screen: open your URLs, Settings, Export/Import, and Quit.
   - The current version is shown at the top of the menu and in Settings.
   - Opening the app again while it is running (from Spotlight, for example) shows Settings.
**Open at login** (on/off in Settings)
**Settings window**
   - Tabs: URLs / Apps / Key Actions / General. Each item is one row (name, target, key, delete).
   - Switch tabs with ← → / Tab, and press ↓ to enter the fields. In the fields, Tab moves and Esc returns to the tabs (⌃Tab switches tabs at any time).
   - The first time, it opens below the 🔗 icon in the menu bar. It remembers where you moved it and its size.
   - Click "?" at the bottom or "Help…" in the menu (⌘H) to see how to use URLL.

### Language

URLL shows English or Japanese depending on your Mac's language setting (Japanese on a Japanese Mac, English otherwise).

---

## Settings Text File Format (Export / Import)

The exported `.txt` file is an easy-to-read text format with one item per line.
The field names are written in the app's language. Both English and Japanese field names can be imported.

```txt
# URLL settings file (v0.008)
List key: ⌃/

---
Name: Google
Key: ⌥G
URL: https://www.google.com

---
Name: Close Tab
Key: ⌥W
Action: ⌘W

---
Name: Terminal
Key: ⌥T
App: /System/Applications/Utilities/Terminal.app
```

### Small differences in writing are OK
- **Full-width and half-width characters**: besides `:` and symbols such as `⌥`, URLL reads full-width colons (`：`), English notation such as `Opt+G`, `Cmd+W` and `Ctrl+/`, and full-width letters and digits (such as `Ｇ`).
- **Several field names**: `Key:` / `Hotkey:`, `Name:` / `Title:`, `URL:` / `App:` / `Action:`, and the Japanese names (`キー:`, `名前:`, `アプリ:`, `キー操作:` and so on) are all accepted.
- **Lines that cannot be read are skipped**: malformed lines, empty lines and comment lines (`#` or `//`) are ignored, and only valid items are imported. URLL tells you about unreadable lines when you import.
- **Key codes are exported too**: the export includes key codes such as `[code:5, mod:2048]`, so importing restores exactly the same keys (you can also delete the codes and write just `Key: ⌥G`).

---

## Settings Storage

- The app ID (bundle ID) is `local.urll`.
- Your URLs and keys are saved in **a settings file named after your user name and the date of the first launch**
  (example: `~/Library/Preferences/urll.alice20261115.plist`).
- That name is stored as `settings_name` in `~/Library/Preferences/local.urll.plist`, and the same file is used from then on.
- To move to another Mac or to make a backup, use **Export Settings…** and **Import Settings…** in the menu.

---

## Accessibility Permission (only for Key Actions, once)

1. In Settings, open the "Key Actions" tab and click "Allow…" (the permission dialog also appears the first time you use a key action)
2. In System Settings → Privacy & Security → Accessibility, turn on **URLL**
3. Back in Settings, it shows "Accessibility is allowed"

If key actions suddenly stop working after you install a new version, remove URLL from the Accessibility list with "−", then add `/Applications/URLL.app` again with "+".

---

## Notes

- Shortcuts work only while the app is running. Turning on Open at login is recommended.
- ⌥ + a letter is normally used to type special characters (such as ∑). While URLL is running, URLL's shortcuts take priority.
- URLL receives its shortcuts first, whatever app you are using. If you set the list key to ⌘/, "Comment line (⌘/)" in Xcode, VS Code and other apps stops working, so the default is ⌃/.
- A key that another app already uses may not be registered. URLL tells you when you save.

---

## Terms of Use

The current version, v0.008, is free to use. Free and paid versions are planned for the future. Copyright (c) 2026 IORI SOFT
