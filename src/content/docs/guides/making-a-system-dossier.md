---
title: Making a System Dossier
sidebar:
    hidden: false
has_children: false
parent: General Guides
pagefind: true
last_modified_date: 2025-01-08
redirect_from: /books/how-to-and-guides/page/making-a-system-dossier
---
## What is a system dossier?
A system dossier is a great way to obtain a large amount of information about your device (Hardware + Software) with relative ease. While listing it all by hand is also an option, several problems require a lot of detailed information to accurately diagnose, and it would be time-consuming to obtain it manually.
## General System Information

{: .info .info-icon }
> If you receive a "Windows protected your PC" popup from SmartScreen running any of the third-party tools below, click `More info` then `Run anyway`.
>
> Windows SmartScreen is a reputation-based check, not an antivirus alert - all executables that Windows doesn't recognize as being trusted and widely used will trigger it. This applies to most of the following tools, as they are not widely used outside of this community.

### Specify
[Specify](https://github.com/Spec-ify) is a tool that gathers information about your OS, software, and hardware, and offers convenient ways to save and share it. 

You can [**download Specify here**](https://spec-ify.com/download)

To use this tool, run `Specify.exe` and follow the prompts. Once done, it will automatically open a link and copy it to your clipboard.
 
Links are automatically deleted after 24 hours. You can choose to redact your username and/or OneDrive commercial name from the report if you feel it's sensitive information.

{: .info.info-icon }
> For machines without internet access, select the `Don't Upload` option. 
> On a machine with internet access, upload `specify_specs.json` to the [**official website**](https://spec-ify.com/) to generate a report.

### Get-Specs

{: .info .info-icon }
> **Note:** This tool is no longer in development, and should only be used as a fallback if [Specify](docs/guides/making-a-system-dossier.html#specify) doesn't work.

Alternatively, you can use [Get-Specs](https://github.com/r-Techsupport/Get-Specs), our legacy tool to get similar information. 

You can [**download Get-Specs here**](https://github.com/r-Techsupport/Get-Specs/releases/latest/download/Get-Specs.zip)



To use this tool, extract `Get-Specs.zip` and run `Specs.cmd` inside the newly extracted folder. Click "Start" and once done, click "Upload" to open a link and copy it to your clipboard, or click "View" to open a `.html` file in your browser. 

Links are automatically deleted after 24 hours. A permanent `TechSupport_Specs.html` file will be generated in the folder regardless.

{: .warning .danger-icon }
> **Do not move, modify, or delete any files inside of the extracted folder.** 

### msinfo32
**`msinfo32`** is a tool built into Windows that provides information about the machine with a focus on hardware, unlike aforementioned tools which focus on both hardware and software.

To use the tool, open the Run dialog by pressing **Win** + **R**, and type in `msinfo32`. Running the tool as an administrator is advisable, but not necessary. 

When saving information from `msinfo32`, you can either:
* **Save:** Create a `.nfo` file which can be opened in `msinfo32` later but is fairly difficult to read manually.
* **Export:** Create a `.txt` file which can't be opened in `msinfo32` but is easier to read manually.

### dxdiag
**`dxdiag`** is a tool built into Windows that primarily provides information about display adapter hardware.

To use the tool, open the Run dialog by pressing **Win** + **R**, and type in `dxdiag`. Running the tool as an administrator is advisable, but not necessary.

To save a `.txt` report file, click "Save All Information"

{: .info .info-icon }
> On machines with internet access, it is recommended to use [**Specify**](http://localhost:4000/docs/guides/making-a-system-dossier.html#specify) to obtain most of the relevant information.

# Useful for crashes or blackscreens
## HWiNFO 
**HWiNFO** is a tool that can be used to obtain and log real-time sensor information such as temperatures, voltages, and component clocks, as well as detailed information about the hardware itself.

You can [**download HWiNFO here**](https://www.fosshub.com/HWiNFO.html)

To install the portable version, right click on the `.zip` file and click "Extract all", then open `HWiNFO64.exe` to launch the program.

### Sensor Logging

***Main Article:*** [**HWiNFO - Full Guide**](/docs/guides/hwinfo)

**To create a real-time log of various system parameters, follow the steps below:**

1. Launch HWiNFO, select `Sensors-only` mode and click "Start". 

2. Click the "Configure Sensors" cog to open the Settings.

3. In the "General" tab, set the desired global sensor polling period. A recommended value is `250` milliseconds, click "OK" to apply the changes.

4. To begin logging, click "Logging Start". You will be prompted to choose the file name/location. Upon clicking "Save", HWiNFO will begin logging to the `.csv` file.

5. To stop logging, click "Logging Stop" or close HWiNFO.

To view the `.csv` file, it's recommended to use [**Hardware Graph Viewer**](https://hw.47c.in/) or [**Generic Log Viewer**](https://www.hwinfo.com/forum/threads/logviewer-for-hwinfo-is-available.802/)

### System Summary

**In addition to sensor logging, HWiNFO can be used to create a detailed system report:**

To create a report: Launch HWiNFO and click "Start", then click "Save Report". 
A dialog will open prompting you to choose the desired file type, and name/path. Clicking "Next" will prompt you to choose what info should be saved. 

{: .info .info-icon }
> To find out how to open and view different file types, refer to the table below:

|File Type|View With|Notes
|:------- |:--- |:--- 
|**`.LOG`**|Text Editors|None
|**`.CSV`**|Spreadsheet Viewers (IE: Excel)|Distinct from [*`.CSV` sensor log files*](/docs/guides/hwinfo), creates a one-time snapshot
|**`.XML`**|Text Editors, `.XML` parsers|Can be converted to more easily viewable file types
|**`.HTML`**|Web Browsers, `.HTML` editors|None
|**`.MHTML`**|Web Browsers, Word, `.HTML` editors|Non-Chromium browsers may require addons to view

## Dump files
***Main Article:*** [**Obtaining BSOD Dumps**](docs/factoids/bsod)

In the event of a Blue Screen of Death (BSOD) or a program crash. Windows will often generate a dump file containing information about the system at the time of the crash, which can be used to analyze the cause.

BSOD Minidump files are located in `C:\Windows\Minidump`. If this folder is absent, make sure [Windows is properly configured to generate minidumps](https://www.tenforums.com/tutorials/5560-configure-windows-10-create-minidump-bsod.html).

Program crash dump files are usually located in `C:\Windows\LiveKernelReports` and `%localappdata%\CrashDump`. Some programs will save dump files in a dedicated folder, often within the program's files.

[**Guide for analyzing BSOD minidumps**]((docs/learning/bsod_guide))

{: .info .info-icon }
> **Note regarding third-party tools:**
>
> We do not recommend third-party programs like [*BlueScreenView*](https://www.nirsoft.net/utils/blue_screen_view.html), [*WhoCrashed*](https://www.resplendence.com/download/whocrashedSetup.exe), and AI-based tools, as they can be highly inaccurate and lack vital context.
> 
> Use official tools like [**WinDbg**](https://aka.ms/windbg/download) to analyze dump files manually.


## Power Supply
When troubleshooting instability/crashing issues or sudden power cuts. It may be useful to identify the model of your Power Supply Unit (PSU)

Unlike most components, PSUs have no ways of communicating their model name to the system, and may need physical inspection in order to be identified.

### Identifying your power supply model (PSU)

{: .caution .warning-icon }
> Before trying to identify the PSU model, ***ensure that no power is going to the system*** by powering off the computer and unplugging the main power cord going to your wall outlet, power strip/extender, or UPS.
>
> If you are not comfortable physically opening your computer, please refer to the steps below for pre-builts.

 1. Remove the side panels from your computer's case. This usually requires a screwdriver, but some cases will use thumbscrews. 

 2. Locate the label on the Power Supply containing the model name and specifications.

 > [**List of common power supply models ranked by quality**](https://cultists.network/140/psu-tier-list/)

### Identifying pre-built power supplies

Pre-built desktops may sometimes use generic OEM power supplies without a clear model name or label, and can be more difficult to disassemble for physical inspection. 
 
In these cases:
* Refer to the manual or product page on the manufacturer's/seller's website to identify the power supply model used.
* Check the receipt to see if the power supply model is listed.

## Useful for networking issues
These are not a replacement for general system information tools, these should only be an additional tool you use.



### ipconfig
ipconfig is a command-line tool built into Windows. This outputs information into the command line and you are responsible for saving it. You can use [pastebin](https://www.pastebin.com), or save it to a text file.

* Running `ipconfig /all` will give information about network adapters and current network connection status.
* Running `ipconfig /displaydns` will give information about currently cached information

### ifconfig.me
ifconfig.me is a site will which give information about your external network connection and status. You can use the command line to get information using the `curl` commands. This outputs information into the command line and you are responsible for saving it. You can use [pastebin](https://www.pastebin.com), or save it to a text file.

* Running `curl ifconfig.me/all` will give give information out external connection status.

If you get the error `Could not resolve host`, just saying that is fine.

## Other, single-task tools
These are not a replacement for general system information tools, these should only be an additional tool you use.

### winver
winver is a tool built into Windows. It will give information about the Windows version, build, and skew.

You can open the tool by typing `winver` into a command line, or you can open it using run (Win+R).

Taking a screenshot, or manually copying the relevant information is acceptable.
* For version and build, you need the line: `Version ____ (OS Build ___.___)`
* For skew, you need the line: `The Windows __ ____ operating system and...`

### slmgr
slmgr is a tool built into Windows. It will give information about the current license and licensing status.

You can open the tool by typing `slmgr /dli` into a command line, or you can open it using run (Win+R).

Most of this information can be useful, it is recommended that you take a screenshot of the window that pops up.

### Crystal disk info
Crystal disk info (CDI) is a tool for obtaining the SMART status of all attached drives.

You can download it [here](https://osdn.net/projects/crystaldiskinfo/downloads/73319/CrystalDiskInfo8_7_0.exe).

For saving information, `Edit` -> `Copy` then either save it to a text file or use [Pastebin](https://www.pastebin.com)
