# Create systemd service
```
sudo vim /etc/systemd/system/docker-core.service
```
# insert below setting
```
[Unit]
Description=Docker Compose Application Service
Requires=docker.service
After=docker.service

[Service]
WorkingDirectory=/home/fw07/docker_compose
ExecStart=/usr/local/bin/docker-compose -f docker-compose-core.yaml up
ExecStop=/usr/local/bin/docker-compose -f docker-compose-core.yaml stop
TimeoutStartSec=0
Restart=always
User=fw07

[Install]
WantedBy=multi-user.target
```

# or this
```
[Unit]
Description=Docker Compose Application Service
Requires=docker.service
After=docker.service
RequiresMountsFor=/dev/STMJOY /dev/MAINJOY /dev/MD
[Service]
WorkingDirectory=/home/fw07/docker_compose
ExecStart=/bin/bash -c 'sleep 5 && /usr/local/bin/docker-compose -f docker-compose-core.yaml up'
ExecStop=/usr/local/bin/docker-compose -f docker-compose-core.yaml stop
TimeoutStartSec=0
Restart=always
User=fw07

[Install]
WantedBy=multi-user.target
```
# reload daemon
```
sudo systemctl daemon-reload
```
# enable & start
```
sudo systemctl enable docker-core.service && sudo systemctl start docker-core.service
```
