---
{"dg-publish":true,"permalink":"/30-interests/tech/disable-app-relaunch-and-window-restore-on-mac/","dgHomeLink":true,"dgPassFrontmatter":false}
---

[[30 interests/Tech/Tech|Tech]]

If you are looking for a way to permanently disable this feature so you don't have to remember the extra "uncheck the box" step every time you turn your machine off, you can simply deny OS X access to the file it uses to store your session state.

Run the following commands:

```bash
# Make the file owned by root (otherwise the OS will just replace it)
sudo chown root ~/Library/Preferences/ByHost/com.apple.loginwindow*

# Remove all permissions, so it can't be read or written to
sudo chmod 000 ~/Library/Preferences/ByHost/com.apple.loginwindow*
```

If you wish to undo this change later and re-enable the feature, perhaps because you've suffered brain damage and now find boot-looping amusing, simply delete this file and the OS will recreate it.

```bash
# Re-enable El Capitan's obnoxious "relaunch all the things" behavior
sudo rm -f ~/Library/Preferences/ByHost/com.apple.loginwindow*
```

---
* source: https://apple.stackexchange.com/questions/230719/how-to-disable-app-relaunch-and-window-restore-in-el-capitan-on-reboot
* tags: [[Mac Tips|Mac Tips]] [[30 interests/Tech/Tech|Tech]], #ready
