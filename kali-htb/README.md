# Kali Linux, Docker och Hack The Box

⚠️ **Viktigt:**
Attackera **endast system som du har tillstånd att testa**.

❗ Installera inte pentesting-verktyg direkt på din egen dator.
Använd alltid en isolerad miljö, till exempel en container eller virtuell maskin.

---

## 🧠 Om detta projekt

För att arbeta med Hack The Box behöver du en Linux-miljö med rätt verktyg, t.ex. Kali Linux.

Du behöver inte använda detta repo eller denna Kali setup för att göra uppgifter.

Denna repo visar hur du kan använda Docker för att köra Kali Linux i en container och ansluta till Hack The Box via VPN.

❗ Om du använder denna docker setup så har du inget grafisk användargränssnitt. Denna setup kör bara med CLI.

## 🚀 Kom igång

### 1. Installera Docker

Ladda ner och installera Docker:
👉 [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

---

### 2. Klona repon

```bash
git clone https://github.com/krullmizter/npods-2026.git
```

Navigera sen in till mappen `/kali-htb`

---

### 3. Bygg Kali-containern

❗ **Se till att Docker är igång innan du fortsätter.**

Inuti `/kali-htb` mappen kör du:

```bash
docker compose up -d
```

⏳ Första gången kan detta ta flera minuter eftersom allt byggs.

Detta ska printas i terminal fönstret då allt är klart:

```bash
Image kali-htb-kali-htb  Built
Network kali-htb_default Created
Container kali-htb       Created
```

---

### 4. Få tillgång till din Kali container

Då `docker compose` har gjort sitt kör då inuti `/kali-htb`:

```bash
docker compose exec kali-htb /bin/bash
```

Nu är du inne i din Kali Linux-miljö, och kan köra diverse kommandon.

---

## 🔐 Anslut till Hack The Box via VPN

### 1. Skapa ett HTB konto

Registrera dig och logga in:
👉 [https://app.hackthebox.com/home](https://app.hackthebox.com/home)

---

### 2. Starta en maskin

Exempel:
👉 [https://app.hackthebox.com/machines/Meow](https://app.hackthebox.com/machines/Meow)

- Klicka på **"Start Machine"**
- Gå till **"Connect with OpenVPN"**

---

### 3. Ladda ner VPN-konfigurations filen till din dator

- Klicka på **"Download VPN"**
- TCP eller UDP spelar ingen roll

---

### 4. Placera filen i rätt mapp

Placera `.ovpn`-filen i:

```
kali-htb/vpn-config/
```

---

### 5. Starta VPN i Kali

Inuti din Kali-container, dom du öppnar med `docker compose exec kali-htb /bin/bash`, kör du:

```bash
openvpn --config /vpn/din-fil.ovpn
```

---

### 6. Öppna en ny terminal

Starta en till Kali container session ifrån mappen som du klonat ner (VPN körs i första):

```bash
docker compose exec kali-htb /bin/bash
```

---

### 7. Kontrollera anslutning

Om allt fungerar ska Hack The Box visa:
✅ **"Connected to Hack The Box"**

Du kan prova köra `ip a` inuti din Kali container för att se om du har en ett interface som heter: `tun0:`

---

## 🧪 Tips

- "Hacking challenges" finns som inlämningsuppgifter i Itslearning
- Använd flera terminaler för effektivare arbete
- Om VPN bryts: starta om `openvpn`

---

## ⚠️ Vanliga problem

**VPN ansluter inte**

- Kontrollera att `.ovpn`-filen ligger i rätt mapp
- Kontrollera filnamnet i kommandot

**Containern startar inte**

- Se till att Docker körs
- Testa:

```bash
docker compose down
docker compose up -d
```
