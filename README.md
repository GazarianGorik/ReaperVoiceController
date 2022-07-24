# I - Setup

1)	Launch Reaper
2)	Go to Options -> Preferences -> Control/OSC/Web
3)	Click add
4)	Under Control surface mode, select OSC (Open Sound Control)
5)	Write your device name
6)	Under Mode, select Configure device IP + local Port
7)	Launch RVC and copy / past corresponding IP and Ports.
8)	Check Allow binding message to REAPER actions and FX learn
9)	Profit!

![image](https://user-images.githubusercontent.com/78812716/180656309-7adb2097-0392-46ce-8e09-0f00505193fb.png)
Note: Your IP or/and ports will probably be different, follow step 7).

# II - Settings window
(1) Settings status: Shows the current state of settings. To save settings you only need to press enter or un-focus the text box you’re editing. Other settings are automatically saved after changes.
(2) Local address IP of the device from where Reaper is used. It’s recommended to use the default IP.
(3) VRC Port: It’s the port used by VRC to receive Reaper’s OSC messages. 
(4) Reaper Port: It’s the port used by Reaper to receive VRC OSC messages. 
Note: You can also set ports manually. It’s recommended to use values between 1025 and 65535. Just keep in mind that to allow connection between Reaper and RVC, both ports need to be free and different.
IMPORTANT NOTE: If you change any connection settings (IP address or ports), you must change them on Reaper side too. Like you’ve done on step 7) of I - Setup.
(5) You can check this box to automatically hide app (settings window) when it’s launched.
(8) If you have any connection troubles or want to check the connection between Reaper and RVC, click this refresh button. More details about connection troubleshooting here V - Troubleshoot connection issues
9) If you catch a bug, send it to me via email, github! It will be fixed ASAP!
![image](https://user-images.githubusercontent.com/78812716/180656376-4f606372-326a-4c7e-9676-123ba7d4572d.png)
(10) To open settings window, double click on the app icon or right click -> settings. 
(11) To turn On / Off RVC, click on the app icon. 

# III - Add / Edit vocal commands
To do so, you need to open and edit commands.csv file from toolbar context menu. Right click on RVC icon and click on Edit commands.csv.
This will automatically open the file in your default .csv file editor (like Excel) and pause the app until you finish editing and CLOSE the file.
![image](https://user-images.githubusercontent.com/78812716/180656401-5c5379cd-fa6b-4b88-ab28-45a45c4bc219.png)
The first column is dedicated to voice commands (it’s recommended to use a pattern (default one is “ok reaper”, to not trigger commands when you talk to someone, or alone… ).
The second column is for OSC addresses and the third one for OSC arguments. More details about how Reaper use OSC messages in Default.ReaperOSC (win + R => “%appdata%\REAPER\OSC”). Note: The first line of this file is ignored, don’t use it!

# IV - Open RVC from Reaper

You can create a toolbar button in Reaper, from which you can open RVC. To do so, create a new Reascript action, copy/paste the following lines, and replace strProgram by the path from which you run RVC (with the correct drive letter).
strProgram = '"X:\\Folder\\AnotherFolder\\ReaperVoiceController.exe"'
strCmd = 'start "" '..strProgram
os.execute(strCmd)

