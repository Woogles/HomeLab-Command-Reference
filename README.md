# Strata Quick Reference Cheat Sheet

> A practical reference for running Strata, local AI models, Hermes Agent integration, and AI development workflows.

---

# Installation

## Linux

```bash
curl -fsSL --connect-timeout 15 --max-time 120 \
https://github.com/Niko1221/Strata/releases/latest/download/install.sh \
-o install.sh && sh install.sh
```

## Windows PowerShell

```powershell
irm -TimeoutSec 120 `
https://github.com/Niko1221/Strata/releases/latest/download/install.ps1 | iex
```

After installation:

```bash
strata launch
```

---

# Core Commands

## Launch Strata

```bash
strata launch
```

Starts the Strata engine and launches your selected model.

---

## Connect External Tools

```bash
strata connect
```

Displays API connection information for:

- Hermes Agent
- Claude Code
- Codex CLI
- OpenCode
- Custom Applications
- OpenAI-Compatible Clients

---

## Update Strata

### Windows

```powershell
UPDATE.bat
```

### Linux

```bash
./update.sh
```

---

# Strata Troubleshooting Commands

## Verify Strata Installation

### Linux

```bash
which strata
```

Shows the installed executable path.

### Verify Version

```bash
strata --help
```

or

```bash
strata version
```

(if supported)

---

# Process Management

## Find Running Strata Processes

```bash
ps aux | grep strata
```

## Find Hermes Processes

```bash
ps aux | grep hermes
```

## Kill a Stuck Process

```bash
kill <PID>
```

Force kill:

```bash
kill -9 <PID>
```

---

# Log Viewing

## Watch Logs Live

```bash
tail -f logfile.log
```

## View Last 100 Lines

```bash
tail -100 logfile.log
```

## Search Logs

```bash
grep ERROR logfile.log
```

```bash
grep WARNING logfile.log
```

---

# System Resource Monitoring

## CPU and Memory

```bash
htop
```

Install:

```bash
sudo apt install htop
```

## Basic Resource Snapshot

```bash
top
```

## RAM Usage

```bash
free -h
```

## Disk Usage

```bash
df -h
```

## Folder Size

```bash
du -sh *
```

---

# NVIDIA Troubleshooting

## GPU Status

```bash
nvidia-smi
```

## Refresh Every Second

```bash
watch -n 1 nvidia-smi
```

## Check Driver Version

```bash
nvidia-smi --query-gpu=driver_version --format=csv
```

## GPU Utilization

```bash
nvidia-smi dmon
```

---

# AMD Troubleshooting

## GPU Information

```bash
rocm-smi
```

## Monitor Live

```bash
watch -n 1 rocm-smi
```

## Verify ROCm

```bash
rocminfo
```

---

# Network Troubleshooting

## Check Listening Ports

```bash
sudo ss -tulpn
```

## Search for API Port

```bash
sudo ss -tulpn | grep 8000
```

## Test Local Endpoint

```bash
curl http://localhost:8000
```

## Verify DNS

```bash
nslookup google.com
```

## Test Connectivity

```bash
ping 8.8.8.8
```

---

# Docker Commands

## Running Containers

```bash
docker ps
```

## All Containers

```bash
docker ps -a
```

## View Logs

```bash
docker logs <container>
```

## Follow Logs Live

```bash
docker logs -f <container>
```

## Restart Container

```bash
docker restart <container>
```

## Enter Container

```bash
docker exec -it <container> bash
```

## Resource Usage

```bash
docker stats
```

---

# Git Commands

## Pull Latest

```bash
git pull
```

## Check Status

```bash
git status
```

## View Remote

```bash
git remote -v
```

## Current Branch

```bash
git branch
```

## Recent History

```bash
git log --oneline -20
```

---

# Whisper Troubleshooting

## Verify Installation

```bash
which whisper
```

## Check Python Package

```bash
pip show openai-whisper
```

## Test Audio File

```bash
whisper sample.wav
```

---

# Python Environment

## Python Version

```bash
python --version
```

## Installed Packages

```bash
pip list
```

## Virtual Environments

```bash
ls ~/.virtualenvs
```

## Active Environment

```bash
which python
```

---

# Storage Management

## Largest Folders

```bash
du -h --max-depth=1 | sort -hr
```

## Largest Files

```bash
find . -type f -exec du -h {} + | sort -hr | head -20
```

## SSD Usage

```bash
df -h
```

---

# Service Management

## Service Status

```bash
systemctl status <service>
```

## Start Service

```bash
sudo systemctl start <service>
```

## Stop Service

```bash
sudo systemctl stop <service>
```

## Restart Service

```bash
sudo systemctl restart <service>
```

## Boot Startup Status

```bash
systemctl is-enabled <service>
```

---

# File Searching

## Find Strata Files

```bash
find / -name "*strata*" 2>/dev/null
```

## Find YAML Files

```bash
find . -name "*.yaml"
```

## Find Campaign*Files

```bash
find ./*ampaigns -type f
```

---

* JSON Validation*
## Validate JSON

```bash
jq .*file.json
```

Install*

```bash
sudo apt install jq
``*

---

# YAML Validation

```bash
*amllint file*yaml
```

Install:

```bash
sudo*apt install yamllint
```

---

#*Performance Diagnostics

## CPU*Information

```bash
l*cpu
```

## Memory*Information

```bash
sudo*dmidecode -* memory
```

## PCI*Devices

```bash
lspci
``*

## GPU Detection

```bash
l*pci | grep VGA
```

---

# Emergen*y Recovery

## Reboot Server

```b*sh
sudo reboot
```

## Shutdown Se*ver

```bash
sudo shutdown now
```*
## Safe Restart of AI Stack

```bash
docker compose down
docker compose up -d
```

or

```bash
systemctl restart hermes
systemctl restart strata
```

---

# Hermes-DM Daily Health Check

```bash
free -h
```

```bash
df -h
```

```bash
nvidia-smi
```

```bash
docker ps
```

```bash
strata connect
```

Confirm:

- GPU recognized
- Sufficient free RAM
- Sufficient SSD space
- Model loaded
- API endpoint responding
- Hermes connected
- Dashboard reachable
- OneDrive sync healthy

# Model Recommendations

## Qwen3.8-Flash-Next

### Recommended Quantizations

| Use Case | Quant |
|-----------|--------|
| Lowest Memory | Q2_0 |
| Daily Use | IQ2_XS |
| Balanced | IQ3_XXS |
| Highest Quality | IQ3_S |
| Coding Focus | IQ1_M |

---

## Unsloth Options

- UD-IQ4_XS
- UD-Q4_K_XL
- UD-Q5_K_XL
- UD-Q6_K_XL
- Q8_0

---

## Gyro Options

- Gyro-S
- Gyro-M

### Notes

- Lower VRAM requirements
- Slower than standard quantizations

---

# API Integration

Strata provides an OpenAI-compatible API endpoint.

## Typical Configuration

| Setting | Value |
|----------|---------|
| Provider | OpenAI Compatible |
| Endpoint | Local Strata URL |
| API Key | Any Value |
| Model | User Defined |

Most third-party applications only require:

- Base URL
- Model Name

---

# Common Workflow

## Start Local AI Stack

```bash
strata launch
```

Wait for model initialization.

---

## View Connection Details

```bash
strata connect
```

Copy endpoint information into:

- Hermes Agent
- Open WebUI
- Continue.dev
- Claude Desktop Proxies
- Custom Applications

---

# Hermes Agent Integration

## Architecture

```text
Players
   │
Voice Input
   │
Whisper
   │
Hermes Agent
   │
Strata
   │
Qwen3.8
   │
Response Generation
```

## Startup Order

1. Start Strata
2. Load model
3. Verify API endpoint
4. Start Hermes Agent
5. Connect dashboard/UI
6. Begin gameplay

---

# Hardware Guidelines

## 12GB GPU

Good For:

- Q2_0
- IQ2_XS

## 16GB GPU

Good For:

- IQ3_XXS
- IQ3_S

## 32GB+ RAM

Recommended minimum.

## 64GB+ RAM

Preferred for:

- Large contexts
- Multi-agent systems
- Better caching performance

## Storage

Recommended:

- NVMe SSD
- 100GB+ free space

Benefits:

- Faster model loading
- Reduced paging delays
- Better large-model performance

---

# Monitoring Checklist

When troubleshooting performance:

## GPU

Check:

- Utilization %
- VRAM Usage
- Temperature
- Power Draw

## System

Check:

- RAM Usage
- CPU Usage
- SSD Activity

## AI Metrics

Check:

- Tokens/Second
- Context Size
- Prompt Processing Speed

---

# Useful Files

| File | Purpose |
|---------|----------|
| START-HERE.bat | First Launch |
| UPDATE.bat | Windows Update |
| setup.sh | Linux Installation |
| update.sh | Linux Update |
| README.md | Main Documentation |
| docs/README.md | Documentation Index |

---

# Common Troubleshooting

## Strata Won't Start

Check:

```bash
strata launch
```

Verify:

- GPU Drivers
- Available VRAM
- Available RAM
- Free Disk Space

---

## Slow Responses

Check:

- Model size
- Context size
- SSD health
- RAM availability

Consider:

- Smaller quantizations
- Reduced context window
- Faster storage

---

## Hermes Can't Connect

Run:

```bash
strata connect
```

Verify:

- Correct API URL
- Agent configuration
- Firewall rules
- Localhost access

---

# Recommended Settings for Hermes-DM

| Component | Recommendation |
|------------|----------------|
| Runtime | Strata |
| Model | Qwen3.8 IQ2_XS |
| STT | Whisper |
| Automation | Hermes Agent |
| Dashboard | Web UI |
| Display | 55" TV |
| Storage | Git + OneDrive Backup |
| Containers | Docker |

---

# Quick Daily Commands

## Launch AI

```bash
strata launch
```

## View Connection Settings

```bash
strata connect
```

## Update System

### Windows

```powershell
UPDATE.bat
```

### Linux

```bash
./update.sh
```

---

# Hermes-DM Startup Checklist

- [ ] Strata Running
- [ ] Model Loaded
- [ ] API Endpoint Verified
- [ ] Hermes Agent Running
- [ ] Whisper Running
- [ ] Dashboard Accessible
- [ ] Campaign Loaded
- [ ] Session State Saved
- [ ] Backup Sync Verified

---

# Helpful References

- GitHub Repository: https://github.com/Niko1221/Strata
- Main Documentation: https://github.com/Niko1221/Strata/tree/main/docs
