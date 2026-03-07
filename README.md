# SPO2 Data Relay — Releases

Pre-compiled release packages for the SPO2 Data Relay Service.

## Download

Go to the [**Releases**](https://github.com/Lifesigns-PD/BPR-releases/releases) page and download the latest `.zip` file.

## Deploy

### One-line installer (latest release)

```bash
curl -fsSL https://github.com/Lifesigns-PD/BPR-releases/releases/latest/download/install.sh | sudo bash
```

### Manual installation

```bash
# 1. Download spo2-relay-vX.X.X-linux-x86_64.zip from the Releases page
# 2. Copy to your Ubuntu 22.04 server

# 3. Extract
unzip spo2-relay-vX.X.X-linux-x86_64.zip

# 4. Deploy (installs Docker, builds container, starts service)
cd spo2-relay-vX.X.X
sudo ./setup.sh

# 5. Verify (use the port selected during setup)
curl http://127.0.0.1:<selected-port>/health
```

> `setup.sh` asks for base URL and relay port during deployment.

See `DEPLOY.md` inside the zip for full instructions.

## What's included

| File | Purpose |
| --- | --- |
| `spo2-relay` | Compiled binary (no Python required) |
| `Dockerfile` | Container definition (non-root, read-only FS) |
| `docker-compose.yml` | Orchestration with security hardening |
| `install.sh` | Bootstrap installer for latest release |
| `setup.sh` | One-command full deployment |
| `firewall.sh` | UFW LAN-only access rules |
| `spo2-relay.service` | systemd auto-start on boot |
| `DEPLOY.md` | Complete deployment instructions |

## Requirements

- Ubuntu 22.04 LTS (server)
- sudo / root access
- Internet connection (for Docker install + outbound HTTPS)
