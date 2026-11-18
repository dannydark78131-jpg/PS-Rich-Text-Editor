PS Rich Text Editor — readme
============================

Files in this folder:
  RichTextEditor.ps1   the editor (single-file PowerShell + WinForms)
  RichTextEditor.ico   stylish app icon (16/32/48/256, PNG-compressed)

Run it (no install needed):
  Right-click RichTextEditor.ps1 > "Run with PowerShell", or from a cmd/PowerShell window:
    powershell -NoProfile -STA -ExecutionPolicy Bypass -File ".\RichTextEditor.ps1"
  (The script auto-relaunches under STA if needed.)

Open a document at launch:
    powershell -NoProfile -STA -ExecutionPolicy Bypass -File ".\RichTextEditor.ps1" "C:\path\to\doc.rtf"

Features:
  - Reads/edits .rtf and .txt; toolbar + Format menu for bold/italic/underline,
    strikethrough, font, text colour, highlight, alignment, bullets.
  - File > Open / Save / Save As; modified-asterisk in title; save-before-close prompt.
  - Status bar: line/column, word count, char count.

Settings (File > Settings...):
  - Install: choose a folder (default %LOCALAPPDATA%\Programs\PSRichTextEditor),
    copies the script + icon there and creates a Start Menu entry. Tick the box
    to also create a desktop shortcut.
  - Desktop shortcut (.lnk) icon colour: click a colour swatch (or "Custom colour...")
    to regenerate the shortcut icon in that colour and refresh the desktop .lnk.
    Note: Windows does not support coloured text per .lnk file; the colour tints
    the shortcut's icon. Buttons to create/refresh or remove the desktop shortcut.
  - Install path and chosen colour persist between runs in
    %LOCALAPPDATA%\PSRichTextEditor\settings.ini.

Icon: the script generates its own multi-size .ico at runtime (same design as
RichTextEditor.ico), so the .ps1 is fully self-contained; the supplied .ico is
for manual use (e.g. pinning, other shortcuts).

ONE-CLICK INSTALL (recommended)
  Keep all files in one folder and double-click Install.bat. It installs
  per-user (no admin) to %LOCALAPPDATA%\Programs\PSRichTextEditor, creates
  Start Menu + Desktop shortcuts with the icon, and registers an
  Add/Remove Programs entry. Uninstall from Settings > Apps, or run
  Uninstall.ps1 from the install folder.

OPTIONAL: build a proper Setup.exe
  Install Inno Setup 6 (jrsoftware.org), then double-click build_installer.bat.
  It compiles installer.iss into dist\PSRichTextEditor-Setup-1.0.0.exe
  (wizard installer with uninstaller).
