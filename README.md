# **Reaper Voice Controller** *(v 0.1)*
This app allows you to trigger REAPER's actions through voice commands.

# How it works?
The app loads a CSV file (editable) which contains some default voice commands and REAPER actions. Commands are detected using the Windows speech recognition engine (offline, and using your default audio device) and actions are sent to REAPER via OSC protocol.

#  Requierement
- Windows 7, 8, 10 (and probably 11, not tested yet)
- [.Net 6.0.5 (x86)](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)

# I - Setup 
1) **[Download](https://github.com/GazarianGorik/ReaperVoiceController/raw/main/ReaperVoiceController.zip)** and extract the app.
2) Launch *REAPER*.
3) Go to *Options* -> *Preferences* -> *Control/OSC/Web* and click *Add*
4) Under *Control surface mode*, select *OSC (Open Sound Control)*.
5) Choose a device name, (ex: *RVC*).
6) Under *Mode*, select *Configure device IP + local Port*.
7) Launch *RVC* and copy / paste corresponding IP and Ports (you can change them if you need to).

Note : Windows Defender may be triggered when you launch the app for the first time, just click on *More info*, then *Run anyway*
(This is caused by the fact that the app don't have digital signature).

<p align="center">
🇫🇷 🥖 🧀 🇫🇷
</p>

<p align="center">
<img width="500" height="468" src="https://user-images.githubusercontent.com/78812716/181577145-cc26d9fb-4171-4618-86cd-71f2731bf067.png">
</p>

<p align="center">
<img width="500" height="468" src="https://user-images.githubusercontent.com/78812716/181577223-7269879f-7c50-4ef9-8f45-c3d535ba66d5.png">
</p>
<p align="center">
🇫🇷 🥖 🧀 🇫🇷
</p>


9) Check *Allow binding message to REAPER actions and FX learn* option.
10) Launch *RVC*, the app will ask you if you want to add optional action to REAPER, which will allow you to check connection between the app and *REAPER*.
11) Profit!

<p align="center">
<img width="559" height="432" src="https://user-images.githubusercontent.com/78812716/181014274-1a6ac2b5-fed2-4a8d-a97a-9bc94e5ef70f.png">
</p>  
<p align="center">
Note: Your IP or/and ports will probably be different, follow step 7).
</p>

# II - Settings window
<p align="center">
<img width="406" height="403" src="https://user-images.githubusercontent.com/78812716/181275378-d2932c08-bcce-44f7-9404-668b5cfb93ac.png">
</p>  

(1) Settings status: Shows the current state of settings. To save settings you only need to press enter or un-focus the text box you’re editing. Other settings are automatically saved after changes.

(2) Local address IP of the device from where Reaper is used. It’s recommended to use the default IP.

(3) VRC Port: It’s the port used by RVC to receive REAPER’s OSC messages. 

(4) Reaper Port: It’s the port used by REAPER to receive VRC OSC messages.

Note: You can set ports manually. It’s recommended to use values between 1025 and 65535. Just keep in mind that to allow connection between REAPER and RVC, both ports need to be free and different.

IMPORTANT NOTE: If you change any connection settings (IP address or ports), you must change them on REAPER too. Like you’ve done on step 7) of [I - Setup](https://github.com/GazarianGorik/ReaperVoiceController/blob/main/README.md#i---setup).

(5) This value defines how strict the command detection algorithm is. Accepted value are between 0.1 and 1 (included). Recommended value are between 0.6 aand 0.8. A too low value may cause the engine to trigger commands even if you don't say the exact command, but with a too high value, you may need to repeat commands, particularly with a poor quality microphone.

(6) You can check this box to automatically hide app (settings window) when the app starts.

(7) Reset settings (not undoable!)

(8) Reset commands (not undoable!)

(9) If you have any connection troubles or want to check the connection between REAPER and RVC, click this refresh button.
More details about connection troubleshooting here [V - Troubleshoot connection issues](https://github.com/GazarianGorik/ReaperVoiceController/blob/main/README.md#v---troubleshoot-connection-issues)

(10) If you catch a bug, click here to send it to me via email or github! It will be fixed ASAP!

<p align="center">
<img width="307" height="195" src="https://user-images.githubusercontent.com/78812716/181558275-ceaffc32-0bed-4540-b53d-d8a0e5066453.png">
</p>  

(11) To open settings window, double click on the app icon or right click -> settings. 

(12) To turn On / Off command detection, click on the app icon. 

# III - Add / Edit vocal commands
To do so, you need to open and edit commands.csv file from toolbar context menu. Right click on RVC icon and click on *Edit commands.csv*.
This will automatically open the file in your default .csv file editor (like Excel) and pause the app until you finish editing and **CLOSE** the file.

<p align="center">
<img width="524" height="226" src="https://user-images.githubusercontent.com/78812716/180656504-a42afbcf-cf97-4990-ad6e-3fb670ff081b.png">
</p>  

The first column is dedicated to voice commands (it’s recommended to use a pattern (default one is “ok reaper”, to not trigger commands when you talk to someone, or alone… 🥲).

The second column is for OSC addresses and the third one for OSC arguments. More details about how REAPER use OSC messages in Default.ReaperOSC file (win + R => “%appdata%\REAPER\OSC”).

Note: The first line of commands.csv is ignored by the app, don’t use it!

# IV - Open RVC from Reaper (OPTIONAL)

You can create a toolbar button in REAPER, from which you can open RVC. To do so, create a new Reascript action, copy/paste the following lines, and replace strProgram value by the path from which you run RVC (with the correct drive letter).
```
strProgram = '"X:\\Folder\\AnotherFolder\\ReaperVoiceController.exe"'
strCmd = 'start "" '..strProgram
os.execute(strCmd)
```

Example:  
<p align="center">
<img width="917" height="73" src="https://user-images.githubusercontent.com/78812716/180656487-40391961-f901-4853-8989-fe99f359d6ee.png">
</p>  

# V - Troubleshoot connection issues

1) Make sure that you’re currently connected to a local network.
2) Verify that your antivirus / firewall is not blocking the app.
3) Try refreshing connection settings.
4) Make sure that Reaper OSC settings match RVC connection settings. (You may have inverted Reaper and RVC ports, try to switch them).
5) Restart RVC.

After following these steps, if the connection is still not established, please report it as a bug.
