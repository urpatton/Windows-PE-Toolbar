# Windows-PE-Toolbar
<p align="center">
  <img src="https://github.com/urpatton/Windows-PE-Toolbar/blob/main/Pictures/WinPE%20Toolbar.jpg?raw=true" />
</p>

## DESCRIPTION
```
Toolbar to simplify Windows PE tasks
```

## FUNCTIONALITY
```
Include in your Windows PE startup process so it autolaunches
Files:
	WinPETool.ps1 - Required file to launch Windows PE toolbar
	AutopilotHash.zip - The AutopilotHash folder and files containing requirements for generating the autopilot hash in PE
	Add the AutopilotHash folder to $env:SystemDrive\AutopilotHash

Buttons:
Clean (diskpart) Drive Button:
	Runs diskpart /s with the "clean" command
Web Browser Button:
	Launches the web browser
	Specify the web browser exe path in $PEToolsform_Load variable $WebBrowserPath
	Specify the web browser URLS in $PEToolsform_Load variable $WebBrowserURL
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
	Runs diskpart /s with the "clean all" command
```
