# Windows-Guide
My Personal Collection of stuff related to windows

# Tools and Resources

[TOC]
## Windows
## Correct logic for a windows system is
- Use enterprise/edu and stay away from home/pro versions (ms basically uses home/pro versions to test KBs and shit on normal users, Ms gives much more fs about OEMs)
- ***Do not legally activate windows*** because it will transmit the most data which are unique (this is far worse than telemetry) use hwidgen
- Uninstall/disable unneeded services/apps (aka debloat)
- Check GPO and change it according to your needs
- Setup Pi-Hole/Adguard home
## Windows 10 (Same Applies to 11)
### What edition / version should I get?
In the following sections various recommended Windows versions are described and explained why they are superior to other similar versions.

#### Windows 10 Education
The *cleanest* semi-annual channel release of Windows 10. Education is the same as Enterprise except features no one uses and is by default configured to not have ads (due to regulations of some countries), so you can go with either if you plan to use a debotnet tool. **Pro Education is not Education, but a worse SKU based on Pro.**
**Difference between EDU and Enterprise**
*For the most part Windows 10 Education is the same as Windows 10 Enterprise… it’s just meant for use in a school environment rather than a business. One feature that’s only available to Windows 10 Enterprise uses is “Long Term Servicing Branch,” which basically means that enterprise customers can postpone Windows updates that provide new features for years, while continuing to receive security updates. Enterprise version is the same as Education edition on features, only if we don’t need to use Store Apps.* [Moreinfo](https://www.microsoft.com/en-us/WindowsForBusiness/Compare)

#### Windows 10 Enterprise LTSC IoT 2021
Windows 10 21H2 based system. Differences from normal Windows 10 Enterprise are the lack of bloat like ads and UWP apps including Windows Store ([can be manually installed](https://forums.mydigitallife.net/threads/guide-add-store-to-windows-10-enterprises-sku-ltsb-ltsc.70741/page-30#post-1468779)) and lack of feature updates (security updates are provided for 10 years). If you aren't bothered by feature upgrades, you might want to get Education instead. Install [VCLibs appx](https://archive.org/download/microsoft.vclibs.140.00-14.0.29231.0-8wekyb3d8bbwe.appx) to restore clipboard and print screen history.

#### What are N / KN editions?
Antitrust laws force Microsoft to provide these editions. N editions are made for Europe and remove Windows Media Player and related features. The later also includes various codecs which may result in YouTube videos not playing among other problems. While the features can be (mostly) restored with an optional update, using these editions is not recommended. KN editions used to be like N but also removing Messenger. Since MSN does not exist anymore, these editions have been discontinued.

#### Changing Windows 10 editions post-install
Windows 10 supports changing SKUs on the fly, however there are some restrictions. First, there are limited upgrade paths, refer to [this matrix](https://en.wikipedia.org/wiki/Windows_10_editions#Commercial_upgrade) for available paths. Second, to change edition Windows must be able to activate the target edition (at least Microsoft says so, sometimes it works without). For us this means you need to install KMS_VL_ALL before changing edition (you might need to set SkipKMS38 to 0 in Activate.cmd if you have a HWIDgen / legit license). After you're done with that, you just need to select and enter the key for the version you want from [here](https://docs.microsoft.com/en-us/windows-server/get-started/kmsclientkeys).

#### Non-Microsoft supported upgrade paths
Microsoft disallows certain upgrade paths that would otherwise work. You can bypass these restrictions by using an ISO and [modifying UpgradeMatrix.xml](https://community.spiceworks.com/topic/2209298-how-to-update-windows-7-8-8-1-enterprise-to-windows-10-ltsc-2019). Remember that this is not supported or tested by Microsoft at all, prepare for the worst.

### Downloading Windows

#### What is an SVF file
An SVF file is a SmartVersion difference patch, essentially the differences of a source and a destination file. Combining it with the source file required yields the destination file (ISOs in our case). These are often used for distributing Windows ISOs, because there is a huge overlap in terms of data between ISOs. Only having to distribute one ISO and 10 GB of SVFs for all edition and language combinations is much easier than 300+ GB of ISOs.

#### How do I extract an SVF file
With [SmartVersion](http://www.smartversion.com/download.htm) (freeware, signed, considered trusted). Download the zip for Windows x86 (x64 and Linux reported to randomly break by some anons, Linux users can just use wine), put smv.exe next to the SVF and the source ISO, open up cmd / PowerShell in the folder (Shift + Right click), and use the following command: `.\smv x <SVF file name> -br .` 
In some links below multiple SVFs might be required to get to your desired edition, just apply them in order.

#### Do I even need an SVF file?
Probably not! Let the filenames guide you: Do you see an ISO matching to what you want to get? If so, you absolutely do not need to do anything with SVF files.

#### Which edition is in which ISO?
* Consumer: Home, Pro, Education (and their N variants)
* Business: Pro, Education, Enterprise (and their N variants)
* LTSC: Enterprise LTSC (and its N variant)

For editions that are in both Consumer and Business there's no difference in content besides the default inserted key (Retail generic vs VL generic).
##Windows Consumer vs Business Editions
![consumer vs business](https://i.imgur.com/fbDMgaR.png)

#### The Installer doesn't let me choose edition or requires key
Make a new file called `ei.cfg` in the `Sources` folder of the installation media with this content:
```
[Channel]
Retail
[VL]
0
```

#### How do I verify ISOs aren't fake / infected?
Microsoft publishes SHA1 or SHA256 for MSDN subscribers. There are numerous automatic dumps of this online where you can look up your hashes, like [here](https://sha1.rg-adguard.net/) and [here](https://www.heidoc.net/php/myvsdump.php). Look up both SHA1 and SHA256 in both of them, since SHA256 is a recent change. If found in any, it's good.

## Links
	https://tb.rg-adguard.net/
	https://tb.rg-adguard.net/products.html	
	https://files.rg-adguard.net/?lang=en-us
	https://techbench.luzea.de/
	https://uupdump.net/
	https://opendirectory.luzea.de/
	https://stuff.mtt-m1.workers.dev/0:/  
#### [Windows MediaCreationTool By AveYo](https://github.com/AveYo/MediaCreationTool.bat)
#### [Windows 10 21H2 Installation Media Tool](https://go.microsoft.com/fwlink/?LinkId=691209)	
#### [Windows 11 Installation Media Tool](https://go.microsoft.com/fwlink/?linkid=2156295)	
#### [Windows 11 Upgrade Assistant](https://go.microsoft.com/fwlink/?linkid=2171764)	
#### [Massgravel's Pastebin](https://pastebin.com/raw/jduBSazJ)
* 10 Enterprise LTSC 2019 (1809 / 2019-03 refresh): [Magnet (en-US only)](magnet:?xt=urn:btih:527ED958E7B901B78BC260DD0BB7364C71D7D403) or [ISOs](https://isofiles.bd581e55.workers.dev/Windows%2010/Windows%2010%20Enterprise%20LTSC%202019/)
* 10 Enterprise LTSC 2021 (21H2): [Magnet (en-US only)](magnet:?xt=urn:btih:29e10fd1688e053aa6a311c31847503ba730772e&dn=Microsoft+Windows+10+IoT+Enterprise+LTSC+2021,+Version+21H2+-+%D0%9E%D1%80%D0%B8%D0%B3%D0%B8%D0%BD%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B5+%D0%BE%D0%B1%D1%80%D0%B0%D0%B7%D1%8B+%D0%BE%D1%82+Microsoft+MSDN+%5BEn%5D&tr=udp://tracker.openbittorrent.com:80&tr=udp://tracker.opentrackr.org:1337/announce) or [ISOs](https://isofiles.bd581e55.workers.dev/Windows%2010/Windows%2010%20Enterprise%20LTSC%202021/)
* Mirrors by luzea: [open directory](https://opendirectory.luzea.de/), [MVS Collection](https://isofiles.bd581e55.workers.dev/)

### Installing Windows

#### Preparing installation media
On Windows you can write the ISO onto a pendrive using [rufus](https://rufus.ie/) or [Ventoy](https://github.com/ventoy/Ventoy/releases)(open source). On Linux use [WoeUSB](https://github.com/slacka/WoeUSB) (open source). No, `dd` doesn't work. If you're on Mac,you can try following [this](https://alexlubbock.com/bootable-windows-usb-on-mac), but you might be better off just using a Windows or Linux machine to make the installer.

### Installation 

#### Installing Windows

1. Select your language, time and keyboard setting, then press next

![image](https://i.imgur.com/u3snrR3.png)

2. Click `Install now`
3. When asked product key select `I don't have a product key`
4. Select `Windows 10 Education` for install, then click `Next`

![image](https://i.imgur.com/ubdIFEu.png)

5. Accept the license terms
6. Select `Custom`

![image](https://i.imgur.com/KqVTvfo.png)

7. If you don't intend to keep any data, delete all partitions. Otherwise delete partitions you don't need (old install, etc..)
8. Select `Unallocated space` and click next. Selecting empty space makes the installer automatically create partitions it needs.

![image](https://i.imgur.com/8JILrYV.png)

9. Wait until it finishes. It might reboot several times during the process.

![image](https://i.imgur.com/6W8Fd0u.png)

#### OOBE

1. Select your region & keyboard
2. When presented the Sign in with Microsoft screen, select `Domain join instead` to avoid logging in

![image](https://i.imgur.com/LUqJM2B.png)

3. Set your username. If you want to avoid having to give recovery questions, don't set a password here, do that later.
4. Disable all sliders on the privacy screen and click `Accept`

![image](https://i.imgur.com/AeuOBbg.png)

5. Reject Cortana when asked
6. Now you should soon be looking at your desktop

![image](https://i.imgur.com/xJB3DZp.png)
#### Common problems
The Windows installer likes to get stuck at partitioning step. If this happens to you, try the following:
* Make sure the installation media is not in an USB3 port - Windows dislikes this sometimes when it doesn't have proper chipset drives yet.
* Remove all storage devices but the installation media and target device - Windows might refuse to install when any disk or disk controller driver is missing, even if it is not needed.
* Run DISKPART's CLEAN command on the target disk. This fixes corrupted or non-existent MBR or GPT. Note that this deletes all partitions.

### Activating Windows
There are various ways of activating activating Windows, some worse, some better.

#### Recommended activators

##### KMS_VL_ALL (by abbodi1406)
[Tutorial](https://rentry.co/dnenp)
Activates volume capable editions of Windows 7 to 10. Uses no internet, networking, tasks, services, servers or drivers. Fully open source, link to source can be found in readme.html in the distribution. Works on all SKUs that can be activated with KMS. You can only activate Office with KMS, so if you plan on installing Office you should probably use this. [Official thread](https://forums.mydigitallife.net/threads/kms_vl_all-smart-activation-script.79535/) (needs registration). Official and updated pastebin from thread is [here](https://pastebin.com/cpdmr6HZ). Use AIO for a nice single .cmd file with menu, or traditional for easier auditing, automation, etc.. [Download Here](https://github.com/abbodi1406/KMS_VL_ALL_AIO/releases)

##### Microsoft Activation Script 
[Tutorial](https://rentry.co/ActivateWin10)
Open Powershell and Run
```
	 irm https://massgrave.dev/get | iex
```
Activator that generates permanent Windows 10 Digital License by faking an update from an older Windows version. Your hardware identifiers are sent to Microsoft, thus the license can survive reinstalls. It can also survive hardware changes if you tie it to a Microsoft account. Cannot activate older Windows, any Office and the following Windows 10 SKUs: Enterprise China Government and all Server SKUs. Ideal for activating normies' computers, since they can't break the activation with AVs or reinstalls. Open source, available on [GitHub](https://github.com/massgravel/Microsoft-Activation-Scripts) and [Gitlab](https://gitlab.com/massgrave/microsoft-activation-scripts). If you plan to install Office it's recommended that you go with KMS_VL_ALL instead, as it adds no overhead to also activate Windows.

#### Windows 10 Versions that can be activated with HWID
	Home (Core)
	CoreCountrySpecific
	Home N (CoreN)
	Home Single Language (CoreSingleLanguage)
	Education
	EducationN
	Enterprise
	EnterpriseN
	EnterpriseS    [LTSB 2015/2016 & LTSC 2019]
	EnterpriseSN   [LTSB 2015/2016]
	Professional
	ProfessionalEducation
	ProfessionalEducationN
	ProfessionalN
	ProfessionalWorkstation
	ProfessionalWorkstationN
	ServerRdsh
	IoTEnterprise
#### Not recommended activators

##### HWIDgen
Works same as Massgrave, but closed source and made by a pretty weird guy. [Official thread with download](https://www.aiowares.com/showthread.php?tid=246) (register only).

##### KMS38
Activation option in HWIDgen for Win10 SKUs that don't support HWIDgen. Activates until 2038. Using it causes repeated trying, timeouting, erroring in event log after renewal interval (not activation interval) passes. Also doesn't support Office. Use KMS_VL_ALL instead.

##### DAZ Loader
Activator for OEM activatable Windows 7 SKUs. Messes with bootloader to inject SLIC tables used for OEM activation, thus also doesn't work with UEFI. Use a KMS compatible edition and KMS_VL_ALL instead. If you already installed a wrong edition with UEFI and really don't want to reinstall, look into [WindSLIC](https://forums.mydigitallife.net/threads/windslic-uefi-slic-injector.29740/).

##### KMSpico, Microsoft Toolkit, etc..
Outdated KMS activators using more bloated, performance hungry and inferior ways compared to KMS_VL_ALL.

##### Random exposed KMS servers on the internet
May go down anytime, which makes all your software unactivated. Also they are usually hosted in nations where exportation is banned by US law like Iran. It is also slower than KMS_VL_ALL since it does actual networking, but this should be obvious.

##### Buying keys on eBay
They are usually not for your region or breaking EULA in other ways (OEM / MAK key, etc..), which makes it about as legal as using any of the other activators. These keys might randomly stop working, possibly after the refund period has expired. Regardless, you might still want to do this for Office, since this is the cheapest possible alternative that requires no persistent software like KMS activators, making it suitable for getting Office for normies' computers. Different regions might require you to use phone activation.

### Installing drivers
As a first step update your Windows, as it sometimes downloads driver updates too. Then, try grabbing all the missing drivers with [SDI Origin](https://sourceforge.net/projects/snappy-driver-installer-origin/). If something doesn't work try downloading the driver from the device manufacturer's site. If it still doesn't work and your computer / laptop is built by an OEM try getting the driver from their site (this sometimes occurs with touchpads of laptops).

### Debloating 
Open Powershell and Run
```sh
	iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/punk99/WinScript/main/Tweak.ps1'))
```
Or use any of the links below 
	[Windows 10 Debloater By Sycnex](https://github.com/Sycnex/Windows10Debloater)
	[Chris Titus Tech Win10Script](https://github.com/ChrisTitusTech/win10script)
	[Optimizer](https://github.com/hellzerg/optimizer)
	[Windows Debloat Script - Sophia Script](https://github.com/farag2/Sophia-Script-for-Windows)

#### Optimize-Offline
Script for removing features from a Windows 10 ISO pre-installation. [Optimize Offline Guide](https://rentry.co/mdl-optimize-guide) (open source). Most changes it does can be done on a live installation in a rollbackable way instead, therefore not recommended for beginners. Doing things wrong or not following the documentation can result in a (subtly) broken install that can only be fixed by reinstalling.

## Microsoft Office
### [***MS Office Setup Tool***](https://github.com/YerongAI/Office-Tool/)
### [**Proposed** explanation and fix for Office C2R **Get genuine** banner](https://infohost.github.io/office-license-is-not-genuine)

## Other Microsoft or Windows related links

### Piracy
* Microsoft stuff: [MDL](https://forums.mydigitallife.net/)
* Software: [nsaneforums](https://www.nsaneforums.com/)
* Games: [rin](https://cs.rin.ru/forum/), [goggames](https://gog-games.com/)

### Other resources
* [MSFN](https://msfn.org/board/) - best Windows-related support forum also harboring projects and their support threads (StartIsBack++, Glass8, OldNewExplorer, UniExtract2, WinNTSetup)
* [VOGONS](https://www.vogons.org/) - forum for retro Windows/DOS; also harbors projects like dgVoodoo and DOSBOX for retro in newer OS stuff.
* [Win-Raid](https://www.win-raid.com/) - drivers / firmware / modding forum; also contains a Windows section with an userbase breaking limits of HW support for pre-10 Windows
* [Station-Drivers](https://www.station-drivers.com/) - also drivers stuff, use if your OEM offers outdated-AF drivers.
* [retrosystemsrevival](https://retrosystemsrevival.blogspot.com/) - download center with software and drivers primarily for retro windows
* [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/) - download center for updates and WHQL drivers without the objectively unnecessary stuff; perfectly navigable only from IE though, due to botched searching by device's IDs & less accurate search results for non-IE browsers.
* [TheHotfixShare](http://thehotfixshare.net/) - mirrors of hotfix updates offered by the recently-defunct Microsoft's Hotfix service
* [reboot.pro](http://reboot.pro/) - also a nice forum for windows stuff and harbor for projects like Ventoy, Rufus or ImDisk
* [AskWoody](https://www.askwoody.com/) - best place for discussing windows updates, bugs and tricks along with general technews; their DEFCON system is nice for tracking whether updates break havoc
* [borncity](https://borncity.com/win/) - nice blog similar to above with a nice FAQ containing tips & tricks that can be useful

## Other programs
###[**Useful Scripts by Abbodi for Windows**](https://github.com/abbodi1406/WHD/tree/master/scripts)

###[**Windows Update Manager**](https://github.com/DavidXanatos/wumgr)

###[***Block The Spot***](https://github.com/mrpond/BlockTheSpot)

###[**Microsoft Store Link Generator**](https://store.rg-adguard.net/)

###[**Windows Terminal Context Menu**](https://github.com/andreivlarox/windowsterminal-shell)

###[Windows DLL Files](http://www.dlldownloader.com/)

###[**AntiSpyTool**](https://github.com/crazy-max/WindowsSpyBlocker)

###**Modernize the About Windows Screen** - [*ModernWinver*](https://github.com/torchgm/ModernWinver)

###[MajorGeeks Windows Tweaks](https://github.com/MajorGeek/MajorGeeks-Windows-Tweaks)

###[Cuztomize Windows Terminal]( https://freshman.tech/windows-terminal-guide/)

###[Icons Wallpaper](https://drive.google.com/drive/folders/1sMmY8KpmjFuruvLQWCE-2Y8x9LlaCPvD)

###[Registry Explorer](https://github.com/zodiacon/RegExp)

###[Aura Sync Fix](https://www.reddit.com/r/ASUS/comments/hzq3ea/support_asus_aura_sync_fix_10779_for_aura_service/)

###[Pokemon Terminal](https://github.com/LazoCoder/Pokemon-Terminal)

###[Taskbar X](https://chrisandriessen.nl/taskbarx)

## Reg Tweaks
### Add Control Panel to File Explorer in Windows 10
```
`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace`
New Key
`{21EC2020-3AEA-1069-A2DD-08002B30309D}` OR `{26EE0668-A00A-44D7-9371-BEB064C98683}`
```
The CLSID code might be different on x86/Win 7 (did not test it).

Open File Explorer, click  This PC  and you will now have direct access to the Control Panel located under the Devices and drives section

### **How to change "About" Infos in Windows 10**
```sh
:: Computer name (PC Name) should not be longer than 15 characters, no spaces either!
reg add "HKLM\System\CurrentControlSet\Control\ComputerName\ActiveComputerName" /v "ComputerName" /t REG_SZ /d "Alpha" /f
reg add "HKLM\System\CurrentControlSet\Control\ComputerName\ComputerName" /v "ComputerName" /t REG_SZ /d "Alpha" /f
reg add "HKLM\System\CurrentControlSet\Services\Tcpip\Parameters" /v "Hostname" /t REG_SZ /d "Alpha" /f
reg add "HKLM\System\CurrentControlSet\Services\Tcpip\Parameters" /v "NV Hostname" /t REG_SZ /d "Alpha" /f

:: Support
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\OEMInformation" /v "Manufacturer" /t REG_SZ /d "BetaBrainz" /f
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\OEMInformation" /v "Model" /t REG_SZ /d "MSI Radeon RX 9999" /f
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\OEMInformation" /v "SupportHours" /t REG_SZ /d "Within 24-48 hours" /f
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\OEMInformation" /v "SupportPhone" /t REG_SZ /d "pepe@gmail.com" /f
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\OEMInformation" /v "SupportURL" /t REG_SZ /d "https://t.me/kakarotdaboss" /f

:: Computer Description
reg add "HKLM\System\CurrentControlSet\services\LanmanServer\Parameters" /v "srvcomment" /t REG_SZ /d "300/30 MBps" /f
```

### **How to change Winver Info in Windows 10 + OEM Win Logo**
```sh
:: System info (The Logo must be in 120x120.bmp)
:: shell:::{BB06C0E4-D293-4f75-8A90-CB05B6477EEE}
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\OEMInformation" /v "Logo" /t REG_SZ /d "D:\Pictures\Logo.bmp" /f
reg add "HKLM\Software\Microsoft\Windows NT\CurrentVersion" /v "RegisteredOrganization" /t REG_SZ /d "BetaBrainz" /f
reg add "HKLM\Software\Microsoft\Windows NT\CurrentVersion" /v "RegisteredOwner" /t REG_SZ /d "The Matrix" /f
```
## **Block Windows major updates**  
```sh
`For 21H1
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate]
"TargetReleaseVersion"=dword:00000001
"TargetReleaseVersionInfo"="21H1"

For 21H2
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate]
"TargetReleaseVersion"=dword:00000001
"ProductVersion"="Windows 10"
"TargetReleaseVersionInfo"="21H2"
```

# Windows 11

##***Windows 11 System Requirements***
![win 11 req](https://i.imgur.com/A9BqudQ.jpeg)

##[Why This PC is Not Compatible With Windows 11](https://github.com/rcmaehl/WhyNotWin11)

##Bypass All checks Windows 11 
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\Setup\LabConfig]
"BypassTPMCheck"=dword:00000001
"BypassSecureBootCheck"=dword:00000001
"BypassRAMCheck"=dword:00000001
"BypassStorageCheck"=dword:00000001
"BypassCPUCheck"=dword:00000001 
```
**OR via cmd as admin**
```sh
reg add "HKLM\SYSTEM\Setup\LabConfig" /v "BypassRAMCheck" /t REG_DWORD /d "1" /f
reg add "HKLM\SYSTEM\Setup\LabConfig" /v "BypassTPMCheck" /t REG_DWORD /d "1" /f
reg add "HKLM\SYSTEM\Setup\LabConfig" /v "BypassSecureBootCheck" /t REG_DWORD /d "1" /f
reg add "HKLM\SYSTEM\Setup\LabConfig" /v "BypassStorageCheck" /t REG_DWORD /d "1" /f
reg add "HKLM\SYSTEM\Setup\LabConfig" /v "BypassCPUCheck" /t REG_DWORD /d "1" /f
```
**Or if your lazy use Open Powershell and Run
```sh
	iex ((New-Object System.Net.WebClient).DownloadString('https://tiiny.tk/TPM'))
```

## Enable Updates on Unsupported Systems
```
; For Upgrades only
[HKEY_LOCAL_MACHINE\SYSTEM\Setup\MoSetup]
"AllowUpgradesWithUnsupportedTPMOrCPU"=dword:00000001
```
**OR via cmd as admin**
```sh
reg add "HKLM\SYSTEM\Setup\MoSetup" /v "AllowUpgradesWithUnsupportedTPMOrCPU" /t REG_DWORD /d "1" /f
```
## **How to disable and remove widgets.exe (news) from Windows 11**
Disable widgets
``` 
`reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v "TaskbarDa" /t REG_DWORD /d "0" /f`
```
Remove Widgets (News/to restore run SFC scan)
```
`takeown /s %computername% /u %username% /f "%ProgramFiles%\WindowsApps\MicrosoftWindows.Client.WebExperience_421.17400.0.0_x64__cw5n1h2txyewy\Dashboard\Widgets.exe"`
`icacls "%ProgramFiles%\WindowsApps\MicrosoftWindows.Client.WebExperience_421.17400.0.0_x64__cw5n1h2txyewy\Dashboard\Widgets.exe" /inheritance:r /grant:r %username%:F`
`taskkill /im Widgets.exe /f`
`del "%ProgramFiles%\WindowsApps\MicrosoftWindows.Client.WebExperience_421.17400.0.0_x64__cw5n1h2txyewy\Dashboard\Widgets.exe" /s /f /q`
```
## ***How to disable Cortana for all User in Windows 11***
```
Get-AppxPackage -allusers Microsoft.549981C3F5F10 | Remove-AppxPackage
```

## **All Windows 11 Registry Uninstall Locations**
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Uninstall

HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall

HKEY_USERS\*\Software\Microsoft\Windows\CurrentVersion\Uninstall

```
## [**Enable Windows Insider Program Without a Microsoft Account**](https://github.com/abbodi1406/offlineinsiderenroll)

## Disable Sign-in screen acrylic (or blur) background 
`reg add "HKLM\Software\Policies\Microsoft\Windows\System" /v "DisableAcrylicBackgroundOnLogon" /t REG_DWORD /d "1" /f`

## Enable Dev Builds
```
; For Dev Builds
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsSelfHost\Applicability]
"BranchName"="Dev"
"Ring"="External"
"ContentType"="Mainline"
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsSelfHost\UI\Selection]
"UIContentType"="Mainline"
"UIBranch"="Dev"
"UIRing"="External"
```

## [Setup Local Account Windows 11 Dev Build 22557+ (Home/Pro)](https://imgur.com/a/bKC0cAA)
** FOR NOW **
- At OOBE
	- press SHIFT + F10 to open cmd
	- `OOBE\BYPASSNRO`

Or

- At OOBE
	- press SHIFT + F10 to open cmd  (might need to try multiple times, a left mouse click might help)
- `net user Admin /add`
- `net localgroup Administrators Admin /add`
- `reg delete HKLM\SOFTWARE\MICROSOFT\WINDOWS\CURRENTVERSION\OOBE /va /f`   
- `net user DEFAULTUSER0 /delete`
- `SHUTDOWN /L`

Or

```
@echo off & title WINDOWS 11 22557+ HOME or PRO setup account without internet connection
:: when the setup halts at OOBE, run via Shift + F10 > D:\user
:: replace D with the media drive letter, or just try E:\user F:\user until you get at it

set /p "name=Enter your account name: "
net user "%name%" /add
net localgroup Administrators "%name%" /add
reg delete "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\OOBE" /va /f
reg delete "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /f /v AutoLogonSID
reg delete "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon" /f /v DefaultUserName
net user defaultuser0 /delete
shutdown /l
```

# ->Miscellaneous Stuff <-
##Other programs
![fwt infograph](https://s1.desu-usergeneratedcontent.xyz/g/image/1562/46/1562467997749.png)

##What Size Keyboard Should i Choose?
![What Size Keyboard to Choose?](https://i.imgur.com/9NLMS8k.png)

##Why is my disk size lower than expected?
***Manufacturers measure capacity in GB or TB whereas pretty much everything else measures it in GiB or TiB while often mislabeling it as GB or TB. The difference is that 1 KB = 1000B while 1 KiB = 1024B, 1MB = 1000000B while 1MiB = 1048576B etc. Based on this alone, 240GB = ~228.8GiB.***
***Filesystem overhead, any kind of filesystem will use some of the disk for its own internal bookkeeping, how much that is varies depending on the filesystem and blocksize used. For a typical NTFS@64k you could expect a few gigabytes lost on a 240GB drive.***
***As a bonus: ISPs and webhosts also measure things in base 10 while also using bits(b) instead of bytes(B). If an ISP promises you 100Mb/s download speed, that really means 100000000b /8 / 1024 / 1024 = 11.92MiB/s***
