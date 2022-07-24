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

![image](https://user-images.githubusercontent.com/78812716/180656634-26f43828-4540-4a6a-9931-2d8ca84d71dc.png)

Note: Your IP or/and ports will probably be different, follow step 7).

# II - Settings window
![image](https://user-images.githubusercontent.com/78812716/180657117-fd099b31-b895-42c7-91e4-552f5bda8ea2.png)

(1) Settings status: Shows the current state of settings. To save settings you only need to press enter or un-focus the text box you’re editing. Other settings are automatically saved after changes.

(2) Local address IP of the device from where Reaper is used. It’s recommended to use the default IP.

(3) VRC Port: It’s the port used by VRC to receive Reaper’s OSC messages. 

(4) Reaper Port: It’s the port used by Reaper to receive VRC OSC messages. 
Note: You can also set ports manually. It’s recommended to use values between 1025 and 65535. Just keep in mind that to allow connection between Reaper and RVC, both ports need to be free and different.
IMPORTANT NOTE: If you change any connection settings (IP address or ports), you must change them on Reaper side too. Like you’ve done on step 7) of I - Setup.

(5) You can check this box to automatically hide app (settings window) when it’s launched.

(8) If you have any connection troubles or want to check the connection between Reaper and RVC, click this refresh button. More details about connection troubleshooting here V - Troubleshoot connection issues

(9) If you catch a bug, send it to me via email, github! It will be fixed ASAP!

![image](https://user-images.githubusercontent.com/78812716/180656742-e4f56819-ef9a-46b6-a484-c438d0809219.png)

(10) To open settings window, double click on the app icon or right click -> settings. 

(11) To turn On / Off RVC, click on the app icon. 

# III - Add / Edit vocal commands
To do so, you need to open and edit commands.csv file from toolbar context menu. Right click on RVC icon and click on Edit commands.csv.
This will automatically open the file in your default .csv file editor (like Excel) and pause the app until you finish editing and CLOSE the file.

![image](https://user-images.githubusercontent.com/78812716/180656504-a42afbcf-cf97-4990-ad6e-3fb670ff081b.png)

The first column is dedicated to voice commands (it’s recommended to use a pattern (default one is “ok reaper”, to not trigger commands when you talk to someone, or alone… ).
The second column is for OSC addresses and the third one for OSC arguments. More details about how Reaper use OSC messages in Default.ReaperOSC (win + R => “%appdata%\REAPER\OSC”). Note: The first line of this file is ignored, don’t use it!

# IV - Open RVC from Reaper

You can create a toolbar button in Reaper, from which you can open RVC. To do so, create a new Reascript action, copy/paste the following lines, and replace strProgram by the path from which you run RVC (with the correct drive letter).
strProgram = '"X:\\Folder\\AnotherFolder\\ReaperVoiceController.exe"'
strCmd = 'start "" '..strProgram
os.execute(strCmd)

Example:  
![image](https://user-images.githubusercontent.com/78812716/180656487-40391961-f901-4853-8989-fe99f359d6ee.png)

# V - Troubleshoot connection issues

1) Make sure that you’re currently connected to a local network.
2) Verify that your antivirus / firewall is not blocking the app.
3) Try refreshing connection settings.
4) Make sure that Reaper OSC settings match RVC connection settings. (You may have inverted Reaper and RVC ports, try to switch them).
5) Restart RVC.
After following these steps, the connection is still not established, please report it as a bug.
