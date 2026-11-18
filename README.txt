PS Rich Text Editor v2.0 — readme
==================================

Files in this folder:
  RichTextEditor.ps1   the editor (single-file PowerShell + WinForms)
  RichTextEditor.ico   stylish app icon (16/32/48/256, PNG-compressed)
  Install.bat          one-click installer launcher
  Install.ps1          one-click installer (per-user, no admin)
  Uninstall.ps1        uninstaller
  Launch.vbs           optional zero-flash launcher (no console window)
  installer.iss        optional Inno Setup script (build a proper Setup.exe)
  build_installer.bat  compiles installer.iss (needs Inno Setup 6)

Run it (no install needed):
  Right-click RichTextEditor.ps1 > "Run with PowerShell", or from a cmd/PowerShell window:
    powershell -NoProfile -STA -ExecutionPolicy Bypass -File ".\RichTextEditor.ps1"
  (The script auto-relaunches under STA if needed.)

Open a document at launch:
    powershell -NoProfile -STA -ExecutionPolicy Bypass -File ".\RichTextEditor.ps1" "C:\path\to\doc.rtf"

WHAT'S NEW IN v2.0
  - Tabbed multi-document editing (Ctrl+N new tab, Ctrl+W close tab,
    Ctrl+Tab next tab, middle-click a tab to close it).
  - Dark / Light theme (View menu, or Settings); persists between runs.
  - Find & Replace (Ctrl+F / Ctrl+H), floating panel, match case / whole word,
    replace all, wraps around.
  - Insert menu: image from file, hyperlink, date & time, horizontal rule.
  - Print & Print Preview (Ctrl+P) — real pagination via EM_FORMATRANGE.
  - Recent files list (File > Recent files), last 10, persisted.
  - Crash-recovery autosave: modified docs are backed up every 20 s; on next
    launch you are offered to restore them. Backups live in
    %LOCALAPPDATA%\PSRichTextEditor\backups.
  - Zoom: Ctrl + mouse wheel, or View > Zoom in/out/reset; shown in status bar.
  - Full-screen / distraction-free mode (F11 or View > Full screen).
  - Font family + font size drop-downs on the toolbar, live-apply.
  - Right-click context menu (undo/cut/copy/paste/format/find).
  - Drag & drop .rtf/.txt files onto the window to open them.
  - Document statistics (Edit > Document statistics): words, chars, paragraphs,
    lines, estimated reading time.
  - Window size/position restored on next launch.
  - Clickable hyperlinks (Ctrl+click opens in default browser).
  - Status bar: line/column, zoom %, modified indicator, words + chars.

Settings (File > Settings...):
  - Appearance: theme (Light/Dark), default font + size.
  - Install: choose a folder (default %LOCALAPPDATA%\Programs\PSRichTextEditor),
    copies the script + icon there and creates a Start Menu entry. Tick the box
    to also create a desktop shortcut.
  - Desktop shortcut (.lnk) icon colour: click a swatch (or "Custom colour...")
    to regenerate the shortcut icon in that colour and refresh the desktop .lnk.
    Note: Windows does not support coloured text per .lnk file; the colour tints
    the shortcut's icon. Buttons to create/refresh or remove the desktop shortcut.
  - Settings persist in %LOCALAPPDATA%\PSRichTextEditor\settings.ini.

Icon: the script generates its own multi-size .ico at runtime (same design as
RichTextEditor.ico), so the .ps1 is fully self-contained; the supplied .ico is
for manual use (e.g. pinning, other shortcuts).

ONE-CLICK INSTALL (recommended)
  Keep all files in one folder and double-click Install.bat. It installs
  per-user (no admin) to %LOCALAPPDATA%\Programs\PSRichTextEditor, creates
  Start Menu + Desktop shortcuts with the icon, and registers an
  Add/Remove Programs entry. Uninstall from Settings > Apps, or run
  Uninstall.ps1 from the install folder.

  The installed shortcuts launch PowerShell with -WindowStyle Hidden, so NO
  console window appears - only the editor GUI. If it fails to start a visible
  error message box appears (and %TEMP%\PSRichTextEditor-crash.log). Launch.vbs
  is included as an optional zero-flash alternative launcher.

OPTIONAL: build a proper Setup.exe
  Install Inno Setup 6 (jrsoftware.org), then double-click build_installer.bat.
  It compiles installer.iss into dist\PSRichTextEditor-Setup-2.0.0.exe
  (wizard installer with uninstaller).
