# Local OpenClaw Setup Guide

Run OpenClaw entirely on your own hardware for maximum privacy and control.

## Why Local?

- **Privacy:** Your data never leaves your machine
- **No API costs:** Use local LLMs (free after setup)
- **Offline capable:** Works without internet
- **Customizable:** Full control over configuration

---

## Hardware Requirements

### Minimum (Basic Usage):
- 8GB RAM
- Modern CPU (4+ cores)
- 20GB free storage

### Recommended (Good Experience):
- 16GB+ RAM
- NVIDIA GPU with 8GB+ VRAM (for local LLMs)
- SSD storage
- Linux or macOS (Windows works via WSL)

### For Running LLMs Locally:
- 32GB+ RAM OR 12GB+ VRAM
- GPU highly recommended

---

## Installation Options

### Option 1: Docker (Easiest)

```bash
# Pull and run
docker run -d \
  --name openclaw \
  -p 18789:18789 \
  -v $(pwd)/workspace:/workspace \
  -v $(pwd)/config:/config \
  openclaw/openclaw:latest
```

### Option 2: NPM (Recommended)

```bash
# Install globally
npm install -g openclaw

# Initialize
openclaw init

# Start
gateway start
```

### Option 3: From Source

```bash
# Clone
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# Install dependencies
npm install

# Build
npm run build

# Start
gateway start
```

---

## Setting Up Local LLMs

### Using Ollama (Easiest)

```bash
# Install Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Pull a small model
ollama pull tinyllama
ollama pull llama3.2:3b

# Start Ollama server
ollama serve
```

### Configure OpenClaw to Use Ollama

Edit `openclaw.json`:

```json
{
  "models": {
    "providers": {
      "ollama": {
        "baseUrl": "http://localhost:11434",
        "models": [
          {
            "id": "tinyllama",
            "name": "TinyLlama",
            "contextWindow": 2048
          },
          {
            "id": "llama3.2:3b",
            "name": "Llama 3.2 3B",
            "contextWindow": 128000
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "ollama/llama3.2:3b"
      }
    }
  }
}
```

---

## Security Hardening

### 1. Firewall Rules

```bash
# UFW (Ubuntu)
ufw default deny incoming
ufw allow 22/tcp    # SSH
ufw allow 18789/tcp # OpenClaw (if needed externally)
ufw enable

# Only allow local access to OpenClaw
ufw deny 18789/tcp
```

### 2. Bind to Localhost Only

```json
{
  "gateway": {
    "bind": "127.0.0.1",
    "port": 18789
  }
}
```

### 3. Authentication

```json
{
  "gateway": {
    "auth": {
      "mode": "token",
      "token": "your-secure-random-token-here"
    }
  }
}
```

### 4. SSH Tunnel for Remote Access

Instead of exposing OpenClaw, use SSH tunnel:

```bash
# From your local machine
ssh -L 18789:localhost:18789 your-server-ip

# Then access via localhost:18789 on your machine
```

---

## Running OpenClaw as a Service

### Systemd (Linux)

Create `/etc/systemd/system/openclaw.service`:

```ini
[Unit]
Description=OpenClaw Gateway
After=network.target

[Service]
Type=simple
User=your-username
WorkingDirectory=/home/your-username/.openclaw
ExecStart=/usr/bin/openclaw gateway start
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```

```bash
# Enable and start
sudo systemctl enable openclaw
sudo systemctl start openclaw
sudo systemctl status openclaw
```

---

## Backup Strategy

### What to Back Up

```bash
# OpenClaw config
cp ~/.openclaw/openclaw.json ~/backups/

# Workspace
cp -r ~/.openclaw/workspace ~/backups/

# Memory files
cp -r ~/.openclaw/workspace/memory ~/backups/
```

### Automated Backup Script

```bash
#!/bin/bash
# backup-openclaw.sh

DATE=$(date +%Y-%m-%d)
BACKUP_DIR="~/backups/openclaw/$DATE"

mkdir -p $BACKUP_DIR
cp ~/.openclaw/openclaw.json $BACKUP_DIR/
cp -r ~/.openclaw/workspace $BACKUP_DIR/

# Keep only last 7 days
find ~/backups/openclaw -type d -mtime +7 -exec rm -rf {} \;
```

---

## Cost Comparison

| Setup | Upfront | Monthly | Best For |
|-------|---------|---------|----------|
| Cloud API | $0 | $20-100+ | Beginners, convenience |
| Local (CPU) | $0 | $0 | Privacy-focused, simple tasks |
| Local (GPU) | $500-2000 | $10 (electricity) | Heavy use, no latency |
| AWS/GCP VM | $0 | $50-200 | Learning, experimentation |

---

## Troubleshooting

### Out of Memory

- Use smaller models (TinyLlama, Phi-3)
- Reduce context window
- Close other applications

### Slow Responses

- Use GPU if available
- Try quantized models (Q4, Q5)
- Reduce max tokens

### Connection Refused

- Check if service is running: `systemctl status openclaw`
- Verify port: `netstat -tlnp | grep 18789`
- Check firewall rules

---

## Next Steps

1. [[Obsidian iOS Sync Setup Guide]] — Sync your notes securely
2. [[OpenClaw Monetization Guide]] — Earn from your setup
3. Research TinyLlama and other small models for AWS cost-cutting

---

*Remember: Local setup = freedom. No one can take away your AI assistant.*
