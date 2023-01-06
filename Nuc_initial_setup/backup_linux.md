# backup ubuntu
- make backup folder on root dir
```
cd /
mkdir whole_backup
```
-tar whole files
```
sudo tar cvpjf /whole_backup/whole_backup_`date +'%Y%m%d_%H%M%S'`.tar.bz2 --exclude=/proc --exclude=/media --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/backup --exclude=/install_files --exclude=/whole_backup /
```

# backup restore
- on root
```
cd /
```
- unzip
```
sudo tar xvpzf /whole_backup/backup.gz -C /
```
