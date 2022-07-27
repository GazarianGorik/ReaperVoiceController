# I - Setup

_1) Launch Reaper._
_2) Go to Options -> Preferences -> Control/OSC/Web._
_3) Click add._
_4) Under Control surface mode, select OSC (Open Sound Control)._
_5) Write any "device" name, (ex: "RVC").
_6) Under Mode, select Configure device IP + local Port.
_7) Launch RVC and copy / paste corresponding IP and Ports (you can change them if you need to).
_8) Check "Allow binding message to REAPER actions and FX learn" option.
_9) Launch Reaper Voice Controller, the app will ask you if you want to add optional action to Reaper, which will allow you to check connection between the _app and REAPER.
_10) Profit!

<p align="center">
<img width="559" height="432" src="https://user-images.githubusercontent.com/78812716/181014274-1a6ac2b5-fed2-4a8d-a97a-9bc94e5ef70f.png">
</p>  
<p align="center">
Note: Your IP or/and ports will probably be different, follow step 7).
</p>

# II - Settings window
<p align="center">
<img width="466" height="463" src="https://user-images.githubusercontent.com/78812716/181275378-d2932c08-bcce-44f7-9404-668b5cfb93ac.png">
</p>  

_(1) Settings status: Shows the current state of settings. To save settings you only need to press enter or un-focus the text box you’re editing. Other _settings are automatically saved after changes.

_(2) Local address IP of the device from where Reaper is used. It’s recommended to use the default IP.

_(3) VRC Port: It’s the port used by VRC to receive Reaper’s OSC messages. 

_(4) Reaper Port: It’s the port used by Reaper to receive VRC OSC messages. 
Note: You can also set ports manually. It’s recommended to use values between 1025 and 65535. Just keep in mind that to allow connection between Reaper and RVC, both ports need to be free and different.
IMPORTANT NOTE: If you change any connection settings (IP address or ports), you must change them on Reaper side too. Like you’ve done on step 7) of I - Setup.

_(5) You can check this box to automatically hide app (settings window) when it’s launched.

_(6) Reset settings (not undoable!)

_(7) Reset commands (not undoable!)

_(8) If you have any connection troubles or want to check the connection between Reaper and RVC, click this refresh button. More details about connection troubleshooting here V - Troubleshoot connection issues

_(9) If you catch a bug, send it to me via email, github! It will be fixed ASAP!

<p align="center">
<img width="339" height="216" src="https://user-images.githubusercontent.com/78812716/181276200-af8a32e6-be1f-44a6-bbd6-de298b7fd60a.png">
</p>  

_(10) To open settings window, double click on the app icon or right click -> settings. 

_(11) To turn On / Off RVC, click on the app icon. 

# III - Add / Edit vocal commands
To do so, you need to open and edit commands.csv file from toolbar context menu. Right click on RVC icon and click on Edit commands.csv.
This will automatically open the file in your default .csv file editor (like Excel) and pause the app until you finish editing and CLOSE the file.

<p align="center">
<img width="524" height="226" src="https://user-images.githubusercontent.com/78812716/180656504-a42afbcf-cf97-4990-ad6e-3fb670ff081b.png">
</p>  

The first column is dedicated to voice commands (it’s recommended to use a pattern (default one is “ok reaper”, to not trigger commands when you talk to someone, or alone… ).
The second column is for OSC addresses and the third one for OSC arguments. More details about how Reaper use OSC messages in Default.ReaperOSC (win + R => “%appdata%\REAPER\OSC”). Note: The first line of this file is ignored, don’t use it!

# IV - Open RVC from Reaper

You can create a toolbar button in Reaper, from which you can open RVC. To do so, create a new Reascript action, copy/paste the following lines, and replace strProgram by the path from which you run RVC (with the correct drive letter).
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

_1) Make sure that you’re currently connected to a local network.
_2) Verify that your antivirus / firewall is not blocking the app.
_3) Try refreshing connection settings.
_4) Make sure that Reaper OSC settings match RVC connection settings. (You may have inverted Reaper and RVC ports, try to switch them).
_5) Restart RVC.
After following these steps, if the connection is still not established, please report it as a bug.
