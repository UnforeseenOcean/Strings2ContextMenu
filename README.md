# Strings2ContextMenu
Windows Explorer context menu entry for Strings2

# Info
A simple registry entry to utilize Strings2, a string dumper program.

# Installation
1. Copy scripts and files into `C:\Strings2`
2. Run `InstallContextMenu.reg`

# Usage
1. Select any file
2. Right click on it
3. Click "Run Strings2"
4. Wait until the CMD window disappears
5. Open `(filename).dumped.txt` in your favorite text editor

# Uninstall
1. Run `UninstallContextMenu.reg`
2. Delete `C:\Strings2` and its contents

# Checksum (SHA-1)
Script (dumpStrings.cmd): `06D1C8FFA5F69EEA96D3B0CE3F303B8B777C8648`
Registry Key for installation: `8A7B11201DFB66564B64473A0ACA6A5D75948E42`
Registry Key for uninstall: `D8263361E793A93DB699E390A2217CEF9A812933`
Strings2 (May 2022 version): `DF186AB88C4E0EA2FF5D5477B2077EC628C42D18`

If you do not trust the version included, please download a new copy from https://github.com/glmcdona/strings2

# Credits
**Strings2 Authors**
- glmcdona/Geoff McDonald
- tarunraji
- tomnudd

# Note about safety
- ALWAYS RENAME EXECUTABLE FILES TO SAFE EXTENSION OR PREVENT EXECUTION.
  - Such as `.exe.vir` or `.cmd.no`
  - I did test the script against many files, but there's no guarantee it's 100% bulletproof
- ALWAYS CHECK FILES BEFORE INSTALLING.
- LOCK THE FILE DOWN TO PREVENT EXECUTABLE SWITCHEROO ATTACK OR SCRIPT INFECTION
  - Utilize Windows' built-in file permissions manager
  - I could not include this edit due to every computer's configuration being different
  - It does pay to check your system regularly for malware, regardless of who you are and how much you know about computer viruses
- TREAT ANY FILE AS HOSTILE UNTIL PROVEN OTHERWISE

# Raw code for the paranoid people
`dumpStrings.cmd`:
```cmd
echo %~1
"C:\Strings2\strings2.exe" "%~1">>"%~1.dumped.txt"
exit
```

`InstallContextMenu.reg`:
```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\*\shell\Run Strings2]
@="Run Strings2"
"Icon"="%SystemRoot%\\System32\\shell32.dll,260"

[HKEY_CLASSES_ROOT\*\shell\Run Strings2\command]
@="\"C:\\Strings2\\dumpStrings.cmd\" \"%1\""

```

`UninstallContextMenu.reg`:
```
Windows Registry Editor Version 5.00

[-HKEY_CLASSES_ROOT\*\shell\Run Strings2]

```
