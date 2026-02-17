# SPO2 Data Relay — Releases

Pre-compiled release packages for the SPO2 Data Relay Service.

## Download

Go to the [**Releases**](https://github.com/Aashish-official/BPR-releases/releases) page and download the latest `.zip` file.

## Deploy

```bash
# 1. Extract
unzip spo2-relay-vX.X.X-linux-x86_64.zip
cd spo2-relay-vX.X.X

# 2. Deploy (installs Docker, builds container, starts service)
chmod +x setup.sh firewall.sh
sudo ./setup.sh

# 3. Verify
curl http://127.0.0.1:8081/health
```

See `DEPLOY.md` inside the zip for full instructions.

## Requirements

- Ubuntu 22.04 LTS (server)
- sudo / root access
- Internet connection (for Docker install + outbound HTTPS)
