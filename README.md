# BringExeToFront
Sets any user-based Window to foreground/focus by ProcessId or -name  
(Release Date: 27.09.2022, Publisher: Dragodraki alias Dreamland, Notice: designed by me and no fork)
<br/>

[<img src="https://user-images.githubusercontent.com/76787321/197257488-1b7aa8e9-9b6f-4600-949e-8ff477cb4bf4.png" width="23%"></img>](https://github.com/Dragodraki/BringExeToFront/releases/latest/download/BringExeToFront.exe)
<br/>

-------------------------------
HOW IT WORKS TECHNICALLY
-------------------------------
By parameter the app detecs whether its about a PID or process name. I recommend search by PID (fast and unique), though in everyday users might have problems to retrieve their PID from an process.

As for process-based identify there isn't any single command for it - you have to make a detour over its PID or the window name. And what if another process or logged-on user has a process with same name? I help myself using the profane build-in *wmic.exe* to list every process with specified name plus current user session and filter the output for either the first or the last value. 
This is why you can activate the first or the last process started with this name. E.g. with "BringExeToFront.exe explorer.exe" you can activate File Explorer and with "BringExeToFront.exe explorer.exe /R" the desktop.

One note to WMIC:
Since wmic.exe is announced to perhaps get removed in the future of Windows 11, there is the little risc of BringExeToFront is going to fail when it comes to process-name-based search. At the moment my Windows 11 still has wmic.exe available by default, but according to MS it could be restrained to OptionalFeatures then.

Setting window as foreground - it may not work if launched from a 'parent' process that isn't in the foreground: Microsoft prevents "stealing" the focus. To make an exception users could setting window as topmost, in general allowing stealing in the registry or pressing ALT key before trying to focus.
My app makes use oft he latter: By sending *ALT keystroke* first and then the standard *SetForegroundWindow(hwnd)* command window becomes foreground and activated even to times when Microsoft would called it "stealing focus".
Hey, after all, you explicit asked BringExeToFront doing so, this is why nobody should bothered it works.


-------------------------------
LICENSE (FREEWARE)
-------------------------------
Permissions:
+ Private and Commcercial usage is allowed as long you don't demand money for it ;)
+ Forks are allowed, but they have to kept free of charge ;)
+ Free Distribution to friends or strangers is allowed, even wanted ;)

Limitations:
- Use the app at your own risk!
- Don't sell it as product or pretend to be its developer!
- Don't abuse it for malicious purposes!


-------------------------------
USAGE
-------------------------------
You have to use either a command-line interface like cmd, powershell, any other console or an automated call from script/program.

Syntax usage:  
- BringExeToFront.exe PID|ProcessName [/Parameter]

Parameters:  
- /R    -> reverse, use first opened process if same name
- /H    -> show this help instead

Examples:  
- BringExeToFront.exe 7032
- BringExeToFront.exe calc.exe
- BringExeToFront.exe calc.exe /R

Hint: Please be aware that Microsoft possible plans to disable WMIC by default in the future. In this case activating window by process name wouldn't be longer possible for BringExeToFront.
