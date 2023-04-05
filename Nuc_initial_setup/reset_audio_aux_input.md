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
sudo nano /usr/local/bin/audio_reset.sh
```
- set shell script
```
#!/bin/bash

timeout_flag=0

# Check if pulseaudio is running
for i in {1..10}
do
    if pgrep pulseaudio > /dev/null; then
        echo "pulseaudio is running"
        timeout_flag=0
        break
    fi
    sleep 1
    if [[ $i -eq 10 ]]; then
        echo "pulseaudio is not running"
        timeout_flag=1
        break
    fi
done

# Kill pulseaudio if it is running
if [ $timeout_flag -eq 0 ]; then
    pulseaudio --kill
    # Wait for pulseaudio to stop
    for i in {1..10}
    do
        if ! pgrep pulseaudio > /dev/null; then
            echo "pulseaudio stopped"
            break
        fi
        sleep 1
        if [[ $i -eq 10 ]]; then
            echo "pulseaudio could not be stopped, force-killing process"
            killall -9 pulseaudio
            break
        fi
    done
fi

# Start pulseaudio
echo "Starting pulseaudio"
pulseaudio --start
```
- add exec auth
```
sudo chmod +x /usr/local/bin/audio_reset.sh
```

# write systemd service script to run shell script
- service script on /etc/systemd/system
```
sudo nano /etc/systemd/system/audio_reset.service
```
- set scripts ( the User section differs from machine name)
```
[Unit]
Description=Restart PulseAudio on boot
After=multi-user.target

[Service]
User=fw06
ExecStart=/usr/local/bin/audio_reset.sh
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
