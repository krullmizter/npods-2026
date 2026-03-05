Kör dessa kommandon i mappen där Dockerfilen finns:

1. `docker compose up -d`
2. `docker compose exec kali-htb /bin/bash`
3. `openvpn --config /vpn/din-konfig-fil.ovpn`
4. Öppna en till CLI till din container för att börja köra kommandon: `docker compose exec kali-htb /bin/bash`
