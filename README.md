# wine flatpak maker with installer e.g., notepad_plus_plus
Create wine64 bit application flatpaks using flatpak-builder and windows app installer

files copied from flathub submission of notepad plus plus.
https://github.com/thejavascriptman/flathub.git

This yaml file builds and installs wine and run the windows setup.
This is similar to `make-flatpak.sh` script of `[flatpak-linux]`

```
flatpak-builder --force-clean build-dir org.notepad_plus_plus.NotepadPlusPlus.yml 
flatpak-builder --user --install --force-clean build-dir org.notepad_plus_plus.NotepadPlusPlus.yml

flatpak run org.notepad_plus_plus.NotepadPlusPlus
flatpak run --command=bash org.notepad_plus_plus.NotepadPlusPlus ; #to check what's inside the flatpak's /app directory
```
###Build a flatpak bundle file from the above built repo:

flatpak-builder --repo="repo" --force-clean "build" org.notepad_plus_plus.NotepadPlusPlus.yaml
flatpak --user remote-add --no-gpg-verify "org.notepad_plus_plus.NotepadPlusPlus" "repo"
flatpak build-bundle "repo" "org.notepad_plus_plus.NotepadPlusPlus.flatpak" org.notepad_plus_plus.NotepadPlusPlus  --runtime-repo="https://flathub.org/repo/flathub.flatpakrepo"

flatpak --user install org.notepad_plus_plus.NotepadPlusPlus.flatpak
flatpak run org.notepad_plus_plus.NotepadPlusPlus
