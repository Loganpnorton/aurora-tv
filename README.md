# Aurora

An Apple TV–style media center for TorBox and Real-Debrid.

## Apps

| | |
|---|---|
| **Android TV / Google TV / phones** | [Aurora.apk](https://github.com/Loganpnorton/aurora-tv/releases/latest/download/Aurora.apk) — updates itself from Settings |
| **Windows** | [Latest installer](https://github.com/Loganpnorton/aurora-tv/releases/latest) (`Aurora-Setup-<version>.exe`) |

Every device works on its own. Add a Home Server to share everything between them.

## Aurora Home Server (optional)

One small service on an always-on computer, NAS or Raspberry Pi keeps your household in sync:

- **Profiles** — everyone gets their own, with an optional PIN
- **Continue Watching, My List and settings** follow each person to every TV, phone and computer, live
- **Pick up anywhere** — "Playing on Living Room TV → Continue Here" resumes on another device and pauses the first
- **Set streaming accounts once** — a household TorBox key / Real-Debrid login every profile can use (no typing keys on a TV)
- **Web app** — optionally serve Aurora to any browser on your network

Video never goes through the server: every device still streams straight from TorBox / Real-Debrid.

### Install — pick one

**Windows** — download [Aurora-Home-Server.exe](https://github.com/Loganpnorton/aurora-tv/releases/latest/download/Aurora-Home-Server.exe) and open it. Setup opens in your browser. Turn on *Start automatically* in its settings to keep it running in the background.

**Linux** (PC, NAS, Raspberry Pi 4/5 — 64-bit):

```sh
curl -fsSL https://github.com/Loganpnorton/aurora-tv/releases/latest/download/install.sh | sh
```

Installs a service that starts at boot. Run the same command again to update.

**Docker** — save [compose.yaml](https://github.com/Loganpnorton/aurora-tv/releases/latest/download/compose.yaml), then:

```sh
docker compose up -d
```

To update later: `docker compose build --pull --no-cache && docker compose up -d`.

Then open **http://&lt;that-machine&gt;:8484** to finish setup (name it, choose a password, add the people in your home).

### Connect your devices

In Aurora on each TV, phone or computer: **Settings › Home Server**. Your server appears automatically — choose it, then pick a profile. If it doesn't appear (some routers, Docker without host networking), choose *Enter Address* and type the address shown on the server's page.

Ports: TCP 8484 (app + sync), UDP 8485 (automatic discovery).
