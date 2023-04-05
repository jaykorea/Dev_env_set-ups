# add pulseaudio nopasswd to visudo
- open visudo
```
sudo visudo
```
- add pulseaudio
```
fw05 ALL=(ALL) NOPASSWD: /sbin/poweroff, /sbin/reboot, /sbin/shutdown, /usr/bin/pulseaudio --kill, /usr/bin/pulseaudio --start

```

# write shell script to kill and run pulseaudio
- write scripts
```
sudo nano /usr/bin/audio_reset.sh
```
- set shell script
```
#!/bin/bash

echo "Audio Resetting, please wait!"

# Kill pulseaudio forcefully using killall
sudo pulseaudio --kill
# Wait for pulseaudio to be terminated
while pgrep -x pulseaudio > /dev/null; do sleep 1; done

# Start pulseaudio using the non-root user specified in the script
sudo pulseaudio --start

exit
```
- add exec auth
```
sudo chmod +x /usr/bin/audio_reset.sh
```

# write systemd service script to run shell script
- service script on /etc/systemd/system
```
sudo nano /etc/systemd/system/audio_reset.service
```
- set scripts
```                                                    
[Unit]
Description=Restart PulseAudio on boot
After=multi-user.target

[Service]
User=fw06
ExecStart=/bin/bash -c "pulseaudio --kill; sleep 5; pulseaudio --start"
Restart=on-failure
Type=simple

[Install]
WantedBy=multi-user.target
```
- reload daemon
```
sudo systemctl daemon-reload
```
- start service
```
sudo systemctl enable audio_reset.service
sudo systemctl start audio_reset.service
```
- check service
```
sudo systemctl status audio_reset.service
```
