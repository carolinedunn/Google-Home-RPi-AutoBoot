# Google-Home-RPi-AutoBoot
How to Automatically Boot your Raspberry Pi 3 into Google Voice Assistant with the AIY Voice Kit

You will need the Google AIY Voice Kit for this project.
Please follow all instructions - https://aiyprojects.withgoogle.com/voice/
and stop AFTER you have verified your project works here - https://aiyprojects.withgoogle.com/voice/#users-guide-3-using-your-device

Open a Terminal on the Raspberry Pi Desktop.

Create the service file. Type:
```
sudo nano /etc/systemd/system/assist.service
```
Copy and paste all text in the assist.service file included in this repository.
```
[Unit]
Description=Assist @ reboot

[Service]
ExecStart=/home/pi/assist.py
User=pi
Group=pi
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=assist

[Install]
WantedBy=multi-user.target
```
Control-X to exit
Y to save
Enter to complete the save.

Enable it (for next boot) by typing in the terminal:
```
sudo systemctl enable assist.service
```

Start it by typing:
```
sudo systemctl start assist.service
```
Reboot your Raspberry Pi
