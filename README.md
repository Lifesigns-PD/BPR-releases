# SPO2 Data Relay — Releases

Pre-compiled release packages for the SPO2 Data Relay Service.

## Download

Go to the [**Releases**](https://github.com/Lifesigns-PD/BPR-releases/releases) page and download the latest `.zip` file for your Ubuntu version:

- `spo2-relay-vX.X.X-linux-ubuntu22.04.zip` for Ubuntu 22.04
- `spo2-relay-vX.X.X-linux-ubuntu24.04.zip` for Ubuntu 24.04

## Deploy

### One-line installer (latest release)

```bash
# Download the appropriate zip for your Ubuntu version from the Releases page
# Then extract and run:
unzip spo2-relay-vX.X.X-linux-ubuntu{22.04|24.04}.zip
cd spo2-relay-vX.X.X
sudo ./install.sh --ubuntu-version {22.04|24.04}
```

### Manual installation

```bash
# 1. Download the appropriate spo2-relay-vX.X.X-linux-ubuntu{22.04|24.04}.zip from the Releases page
# 2. Copy to your Ubuntu server

# 3. Extract
unzip spo2-relay-vX.X.X-linux-ubuntu{22.04|24.04}.zip

# 4. Deploy (installs Docker, builds container, starts service)
cd spo2-relay-vX.X.X
sudo ./install.sh --ubuntu-version {22.04|24.04}

# 5. Verify (use the port selected during setup)
curl http://127.0.0.1:<selected-port>/health
```

> `install.sh` asks for base URL and relay port during deployment. Use `--ubuntu-version` to specify your Ubuntu version (22.04 or 24.04).

See `DEPLOY.md` inside the zip for full instructions.

## What's included

| File | Purpose |
| --- | --- |
| `spo2-relay` | Compiled binary (no Python required) |
| `Dockerfile` | Container definition (non-root, read-only FS) |
| `docker-compose.yml` | Orchestration with security hardening |
| `install.sh` | Bootstrap installer (accepts `--ubuntu-version`) |
| `setup.sh` | One-command full deployment |
| `firewall.sh` | UFW LAN-only access rules |
| `spo2-relay.service` | systemd auto-start on boot |
| `DEPLOY.md` | Complete deployment instructions |
| `packages/` | Offline Debian packages for your Ubuntu version |

## Requirements

- Ubuntu 22.04 LTS or 24.04 LTS (server)
- sudo / root access
- Internet connection during initial setup (for Docker install + outbound HTTPS); fully offline after deployment
