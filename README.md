# plex
```
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/plex.sh)"
```
You need to claim the new server
```
use this link to get code:
https://account.plex.tv/claim
add this in the lxc or docker container
curl -X POST "http://localhost:32400/myplex/claim?token=YOUR_CLAIM_TOKEN_HERE"
```
