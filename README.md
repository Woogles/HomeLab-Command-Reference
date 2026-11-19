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
