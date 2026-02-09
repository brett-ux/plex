# Plex
## Install helper script
```
https://community-scripts.github.io/ProxmoxVE/scripts?id=plex&category=Media+%26+Streaming
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/plex.sh)"
```
## You need to claim the new server
```
use this link to get code:
https://account.plex.tv/claim
add this in the lxc or docker container:
curl -X POST "http://localhost:32400/myplex/claim?token=YOUR_CLAIM_TOKEN_HERE"
```
## Mounting NAS on Proxmox host
In the GUI, go to Datacenter section, then Storage, then Add
ID: nas-media
Server: 192.168.5.22
Export: /mnt/NAS/Storage01
### Mounting on Container Host
```
nano /etc/pve/lxc/<CTID>.conf
```

Add this to the end of the Config File
```
mp0: /mnt/pve/nas-media,mp=/mnt/media,ro=1
```


## Debian LXC Install
Add Repos
```
nano /etc/apt/sources.list
```

```
deb http://deb.debian.org/debian bookworm main contrib non-free non-free-firmware
deb http://deb.debian.org/debian bookworm-updates main contrib non-free non-free-firmware
deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
```
Download from Plex website
```
https://www.plex.tv/media-server-downloads/?cat=computer&plat=linux
```

```
cd /tmp
wget https://downloads.plex.tv/plex-media-server-new/1.42.2.10156-f737b826c/debian/plexmediaserver_1.42.2.10156-f737b826c_amd64.deb

```

```
apt install ./plexmediaserver_1.42.2.10156-f737b826c_amd64.deb
```

```
systemctl enable plexmediaserver
systemctl start plexmediaserver
systemctl status plexmediaserver
```
