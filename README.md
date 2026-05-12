# iTerm2 Config

Full iTerm2 preferences tracked as XML, loaded automatically via iTerm2's custom preferences folder feature.

## How it works

iTerm2 is configured to read and write its preferences from `~/.config/iterm2/` instead of `~/Library/Preferences/`. This means any setting changed through the iTerm2 UI is written directly into this repo.

Bootstrap (handled by [initialize/setup.sh](https://github.com/cgoolsby/initialize)):

```
clone iterm2 → ~/.config/iterm2/
  └── defaults write LoadPrefsFromCustomFolder → true
  └── defaults write "Custom Folder" → ~/.config/iterm2
```

On next iTerm2 launch it reads `com.googlecode.iterm2.plist` from this folder.

## Key bindings

| Shortcut | Action |
|---|---|
| ⌥ ← | Word backward |
| ⌥ → | Word forward |
| ⌘ ← | Beginning of line |
| ⌘ → | End of line |

## Keeping the repo up to date

After changing settings in iTerm2, convert the plist back to XML before committing (iTerm2 writes binary):

```bash
plutil -convert xml1 ~/.config/iterm2/com.googlecode.iterm2.plist
git add com.googlecode.iterm2.plist
git commit -m "update iTerm2 preferences"
git push
```
