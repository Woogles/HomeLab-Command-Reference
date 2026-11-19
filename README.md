# Strata Operations & Reference Manual

> Comprehensive reference for Strata installation, operation, troubleshooting, monitoring, API integration, Hermes Agent workflows, and Hermes-DM deployment.

---

# Table of Contents

- Installation
- Core Commands
- Model Selection
- API Integration
- Hermes Agent Integration
- Hardware Recommendations
- Monitoring & Diagnostics
- Troubleshooting Commands
- Docker Commands
- Git Commands
- Whisper Commands
- Python Environment
- Storage Management
- Service Management
- File Searching
- JSON & YAML Validation
- Performance Diagnostics
- Emergency Recovery
- Daily Health Checks
- Hermes-DM Startup Checklist

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

## First Launch

```bash
strata launch
```

---

# Core Strata Commands

## Launch Strata

```bash
strata launch
```

Launches the Strata engine and model selection interface.

---

## View Connection Information

```bash
strata connect
```

Displays API endpoint information for:

- Hermes Agent
- Claude Code
- OpenCode
- Codex CLI
- OpenAI Compatible Clients
- Custom Applications

---

## Help

```bash
strata --help
```

Displays command help and available options.

---

## Verify Installation

Linux:

```bash
which strata
```

Windows:

```powershell
where strata
```

---

## Version Information

```bash
strata version
```

If supported by installed version.

---

# Updating Strata

## Windows

```powershell
UPDATE.bat
```

## Linux

```bash
./update.sh
```

---

# Model Selection

## Recommended: Qwen3.8-Flash-Next

### Quantizations

| Use Case | Quant |
|-----------|--------|
| Minimal Memory | Q2_0 |
| Daily Driver | IQ2_XS |
| Balanced | IQ3_XXS |
| Higher Quality | IQ3_S |
| Coding Focus | IQ1_M |

---

## Unsloth Quantizations

- UD-IQ4_XS
- UD-Q4_K_XL
- UD-Q5_K_XL
- UD-Q6_K_XL
- Q8_0

---

## Gyro Models

- Gyro-S
- Gyro-M

Advantages:

- Lower memory usage

Tradeoff:

- Slower inference speed

---

# API Integration

Strata provides OpenAI-compatible APIs.

## Typical Configuration

| Setting | Value |
|----------|---------|
| Provider | OpenAI Compatible |
| Endpoint | Local Strata URL |
| API Key | Any Value |
| Model | User Selected |

---

# Hermes Agent Integration

## Example Architecture

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
Campaign Response
```

---

## Startup Sequence

1. Start Strata
2. Load Model
3. Run `strata connect`
4. Start Hermes Agent
5. Verify API Connection
6. Launch Dashboard
7. Begin Session

---

# Hardware Recommendations

## GPU

### 12GB VRAM

Recommended:

- Q2_0
- IQ2_XS

### 16GB+ VRAM

Recommended:

- IQ3_XXS
- IQ3_S

---

## Memory

### Minimum

```text
32 GB RAM
```

### Recommended

```text
64 GB RAM
```

### Preferred for Multi-Agent Systems

```text
128 GB RAM+
```

---

## Storage

Recommended:

```text
NVMe SSD
100GB+ Free Space
```

Benefits:

- Faster loading
- Reduced paging delays
- Better large-model performance

---

# Monitoring & Diagnostics

## CPU Usage

```bash
top
```

Better:

```bash
htop
```

Install:

```bash
sudo apt install htop
```

---

## Memory Usage

```bash
free -h
```

---

## Disk Space

```bash
df -h
```

---

## Directory Sizes

```bash
du -sh *
```

---

# Process Management

## Locate Running Strata Processes

```bash
ps aux | grep strata
```

---

## Locate Hermes Processes

```bash
ps aux | grep hermes
```

---

## Locate Python Processes

```bash
ps aux | grep python
```

---

## Kill Process

```bash
kill PID
```

---

## Force Kill Process

```bash
kill -9 PID
```

---

# Log Analysis

## Follow Logs

```bash
tail -f logfile.log
```

---

## Last 100 Lines

```bash
tail -100 logfile.log
```

---

## Search for Errors

```bash
grep ERROR logfile.log
```

---

## Search for Warnings

```bash
grep WARNING logfile.log
```

---

## Search for Exceptions

```bash
grep Exception logfile.log
```

---

# NVIDIA GPU Commands

## GPU Status

```bash
nvidia-smi
```

---

## Continuous Monitoring

```bash
watch -n 1 nvidia-smi
```

---

## Driver Version

```bash
nvidia-smi --query-gpu=driver_version --format=csv
```

---

## GPU Metrics

```bash
nvidia-smi dmon
```

---

# AMD GPU Commands

## GPU Status

```bash
rocm-smi
```

---

## Continuous Monitoring

```bash
watch -n 1 rocm-smi
```

---

## ROCm Verification

```bash
rocminfo
```

---

# Network Diagnostics

## Listening Ports

```bash
sudo ss -tulpn
```

---

## Search Specific Port

```bash
sudo ss -tulpn | grep 8000
```

---

## Test Endpoint

```bash
curl http://localhost:8000
```

---

## DNS Test

```bash
nslookup google.com
```

---

## Connectivity Test

```bash
ping 8.8.8.8
```

---

## View Open Connections

```bash
netstat -tulpn
```

---

# Docker Reference

## Running Containers

```bash
docker ps
```

---

## All Containers

```bash
docker ps -a
```

---

## View Logs

```bash
docker logs CONTAINER
```

---

## Follow Logs

```bash
docker logs -f CONTAINER
```

---

## Restart Container

```bash
docker restart CONTAINER
```

---

## Enter Container

```bash
docker exec -it CONTAINER bash
```

---

## Resource Usage

```bash
docker stats
```

---

## Stop All Containers

```bash
docker stop $(docker ps -q)
```

---

## Docker Compose Start

```bash
docker compose up -d
```

---

## Docker Compose Stop

```bash
docker compose down
```

---

# Git Reference

## Check Status

```bash
git status
```

---

## Pull Updates

```bash
git pull
```

---

## Current Branch

```bash
git branch
```

---

## View Remotes

```bash
git remote -v
```

---

## Commit History

```bash
git log --oneline -20
```

---

## Latest Changes

```bash
git diff
```

---

# Whisper Commands

## Verify Installation

```bash
which whisper
```

---

## Package Info

```bash
pip show openai-whisper
```

---

## Speech Test

```bash
whisper sample.wav
```

---

# Python Environment

## Version

```bash
python --version
```

---

## Installed Packages

```bash
pip list
```

---

## Active Interpreter

```bash
which python
```

---

## Active Virtual Environment

```bash
echo $VIRTUAL_ENV
```

---

# Storage Management

## Top Folders

```bash
du -h --max-depth=1 | sort -hr
```

---

## Top Files

```bash
find . -type f -exec du -h {} + | sort -hr | head -20
```

---

## Available Space

```bash
df -h
```

---

# Service Management

## Service Status

```bash
systemctl status SERVICE
```

---

## Start Service

```bash
sudo systemctl start SERVICE
```

---

## Stop Service

```bash
sudo systemctl stop SERVICE
```

---

## Restart Service

```bash
sudo systemctl restart SERVICE
```

---

## Enable At Boot

```bash
sudo systemctl enable SERVICE
```

---

## Verify Boot Status

```bash
systemctl is-enabled SERVICE
```

---

# File Searching

## Find Strata Files

```bash
find / -name "*strata*" 2>/dev/null
```

---

## Find YAML Files

```bash
find . -name "*.yaml"
```

---

## Find JSON Files

```bash
find . -name "*.json"
```

---

## Find Campaign Files

```bash
find ./campaigns -type f
```

---

# JSON Validation

## Install JQ

```bash
sudo apt install jq
```

---

## Validate JSON

```bash
jq . file.json
```

---

# YAML Validation

## Install Yamllint

```bash
sudo apt install yamllint
```

---

## Validate YAML

```bash
yamllint file.yaml
```

---

# Performance Diagnostics

## CPU Information

```bash
lscpu
```

---

## Memory Information

```bash
sudo dmidecode -t memory
```

---

## PCI Devices

```bash
lspci
```

---

## GPU Detection

```bash
lspci | grep VGA
```

---

## Kernel Information

```bash
uname -a
```

---

## OS Information

```bash
cat /etc/os-release
```

---

# Emergency Recovery

## Reboot

```bash
sudo reboot
```

---

## Shutdown

```bash
sudo shutdown now
```

---

## Restart Docker Stack

```bash
docker compose down
docker compose up -d
```

---

## Restart Services

```bash
sudo systemctl restart hermes
sudo systemctl restart strata
```

---

# Daily Health Check

Run these every morning:

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

Verify:

- GPU Detected
- VRAM Available
- RAM Available
- SSD Space Available
- Model Loaded
- API Endpoint Active
- Hermes Connected
- Dashboard Accessible
- OneDrive Sync Healthy

---

# Hermes-DM Startup Checklist

- [ ] Strata Running
- [ ] Model Loaded
- [ ] GPU Healthy
- [ ] API Endpoint Verified
- [ ] Hermes Agent Running
- [ ] Whisper Running
- [ ] Dashboard Accessible
- [ ] Campaign Loaded
- [ ] Session State Saved
- [ ] Docker Containers Healthy
- [ ] Git Repository Synced
- [ ] OneDrive Sync Verified
- [ ] Backup Completed

---

# Quick Command Summary

```bash
# Launch Strata
strata launch

# View API settings
strata connect

# GPU status
nvidia-smi

# Memory usage
free -h

# Disk usage
df -h

# Running containers
docker ps

# Service status
systemctl status SERVICE

# Follow logs
tail -f logfile.log

# Git status
git status

# YAML validation
yamllint file.yaml

# JSON validation
jq . file.json
```

---
**Project:** Hermes-DM  
**Runtime:** Strata + Qwen3.8  
**Agent Framework:** Hermes Agent  
**Voice Input:** Whisper  
**Deployment Platform:** Ubuntu Linux + Docker
