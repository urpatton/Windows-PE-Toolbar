# Windows-PE-Toolbar
<p align="center">
  <img src="https://github.com/urpatton/Windows-PE-Toolbar/blob/main/Pictures/WinPE%20Toolbar.jpg?raw=true" />
</p>

## DESCRIPTION
```
Toolbar to simplify Windows PE tasks

PARAMETER WebBrowserPath
(Optional) Specify the Windows PE path for a built-in web browser (I reccomend Pale Moon Portable - Link below)

PARAMETER WebBrowserURL
(Optional) Specify a URL for the web browser. Default is www.google.com if -WebBrowerURL is not specified or is empty.

PARAMETER AllowClose
Allows the toolbar to be closed
Default: "False"
Accepted input: "True"
```

## EXAMPLE
```
------ Example 1 ------
Launch without a browser or url specified
WinPETool.ps1

------ Example 2 ------
Launch with a browser and url specified
WinPETool.ps1 -WebBrowserPath "X:\Program Files\PaleMoon\PaleMoon.exe" -WebBrowserURL "https://www.google.com"

------ Example 3 ------
Launch with browser but no url (will default to www.google.com)
WinPETool.ps1 -WebBrowserPath "X:\Program Files\PaleMoon\PaleMoon.exe"

------ Example 4 ------
Launch with option to allow closeing
WinPETool.ps1 -AllowClose True
```

## NOTES
```
Include in your Windows PE startup process so it autolaunches
Created to simplify common Windows PE tasks for people who are unfamilar with Windows PE.
```

## FUNCTIONALITY
```
Toolbar can not be closed by default. Use "-AllowClose" to enable the "X" close control box.

Files:
WinPETool.ps1 - Required file to launch Windows PE toolbar
AutopilotHash.zip - The AutopilotHash folder and files containing requirements for generating the autopilot hash in PE
dpscript.txt - Created when the Clean Drive button is clicked, location - $env:SystemDrive\Windows\System32
dpdodscript.txt - Created when the Secure Disk Erase button is clicked, location - $env:SystemDrive\Windows\System32
AutopilotHWIDHash-SerialNumber.csv - Created when Autopilot Hash button is clicked, location - $env:SystemDrive\AutopilotHash

Buttons:
Clean (diskpart) Drive Button:
Runs diskpart /s dpscript.txt with the "clean" command

Web Browser Button:
Launches the web browser (I reccomend Pale Moon Portable - Link below)
Assumes YourBrowser.exe takes input directly as "YourBrowser.exe www.google.com" to launch directly to www.google.com
Specify the web browser exe path in $PEToolsform_Load variable $WebBrowserPath
Specify the web browser URLS in $PEToolsform_Load variable $WebBrowserURL
For browser launch issues see "#TODO: Launch Web Browser" under "$WebBrowserbutton_Click"
Button is disabled if WebBrowserPath is not specified or the path is not found

Explorer and DaRT Tools Button:
Launches the Windows PE DaRT toolset (Microsoft Diagnostics and Recovery Toolset)
Require the DaRT tools exe and DartConfig.dat to exist.
Button is disabled if files are missing

Autopilot Hash Button:
Generates the Autopilot hash and writes it to the folder $env:SystemDrive\AutopilotHash
Requires files (included in AutopilotHash.zip:
"$env:SystemDrive\Windows\System32\PCPKsp.dll"
"$env:SystemDrive\AutopilotHash\oa3tool.exe"
"$env:SystemDrive\AutopilotHash\OA3.cfg"
Button is disabled if files are missing

Kill Deployment Button:
Stops all running deployment processes and forces an immediate restart
TsManager.exe
TsmBootstrap.exe
TsProgressUI.exe
cscript.exe
Wscript.exe

Secure Disk Erase Button:
Runs diskpart /s dpdodscript.txt with the "clean all" command
```

## LINK
```
Pale Moon Portable - https://www.palemoon.org/download.shtml (Select the "Portable Windows Versions")
```

## CHANGELOG
```
v1.1
Fixed bug with disk wipe causing disk wipe and secure wipe to continue when no disk number was input
```
