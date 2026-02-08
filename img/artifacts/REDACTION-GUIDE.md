# Screenshot Redaction Guide

This guide documents what sensitive information needs to be redacted from dashboard screenshots before use on the consulting website.

---

## Overview

| Image | Priority | Sensitivity |
|-------|----------|-------------|
| `v2-dashboard.jpg` | 🔴 HIGH | Contains file paths, model names, token counts, personal agent names |
| `dashboard-main.jpg` | 🟠 MEDIUM | Model names, session IDs, token counts |
| `topology-real.jpg` | 🟠 MEDIUM | Same as dashboard-main (duplicate image) |
| `topology-blue.jpg` | 🟠 MEDIUM | Same as dashboard-main (duplicate image) |
| `v1-dashboard.jpg` | 🟢 LOW | Minimal sensitive info, mostly news headlines |

---

## Image-by-Image Redaction

### 1. `v2-dashboard.jpg` (EZRA Command Center) — HIGH PRIORITY

**Critical elements to redact:**

| Location | Current Text | Replace With |
|----------|--------------|--------------|
| Header | "EZRA" | "CLAW" or "AGENT HUB" |
| Error banner | File path `/Users/al/openclaw/agents/main/agent/auth-profiles.json` | `/path/to/config.json` |
| Session tiles | "Telegram A A id:7969283458 2026-02-04 0..." | "Channel Session 2026-02-04" |
| Session tiles | "llama-3.1-nemotron-ultra-253b-v1" | "Primary LLM" |
| Session tiles | "llama-3.1-nemotron..." badges | "LLM" or blur |
| Subagent names | "strategic advisor for an AI agent named Ezra (Chie..." | "Strategic Advisor" |
| Subagent names | "polymarket-research-dispatch" | "Research Dispatch" |
| Subagent names | "whale-tracker" | "Market Tracker" |
| Subagent names | "synthesizer-followup" | "Synthesizer" |

**Token Usage Section (bottom):**

| Current Label | Replace With |
|---------------|--------------|
| LOCAL: 4.7M | LOCAL: ███ |
| GEMINI: 125.1M | CLOUD-A: ███ |
| ANTHROPIC: 2.1M | CLOUD-B: ███ |
| OPENAI: 13.2M | CLOUD-C: ███ |
| OPENROUTER: 8.0M | ROUTER: ███ |
| NVIDIA: 1.2M | GPU-API: ███ |
| GOOGLE-ANTIGRAVITY: 18.3M | CUSTOM: ███ |
| NVIDIA-PROXY: 0 | PROXY: ███ |

**Compute Section:**

| Current | Replace With |
|---------|--------------|
| 13.3 GB VRAM | ██ GB VRAM |
| llama3.2, qwen2.5 | "Local Model A", "Local Model B" |
| $0.00 | Keep or blur |

**Alert Messages:**

| Current | Replace With |
|---------|--------------|
| `/Users/al/openclaw/workspace/skills/...` | `/workspace/skills/...` |
| "Telegram requires target <chatId>" | "Channel requires target" |
| "provider 'ollama'" | "provider 'local'" |

---

### 2. `dashboard-main.jpg` / `topology-real.jpg` / `topology-blue.jpg` (Agent Exhaust)

These three images appear identical. Redact once, apply to all.

**Model Usage Chart (bottom left):**

| Current Model | Replace With |
|---------------|--------------|
| claude-opus-4-0 | Primary LLM |
| gemini-2.5-flash | Cloud LLM A |
| gemini-3-flash | Cloud LLM B |
| gpt-4o-mini | Cloud LLM C |
| deepseek-v3.2 | Cloud LLM D |
| gemini-3-flash | Cloud LLM E |
| deepseek-v3.1 | Cloud LLM F |

**Top Sessions Table:**

| Column | Action |
|--------|--------|
| SESSION (IDs like 53ad9498) | Blur or replace with "session-001", "session-002" |
| MODELS column badges | Replace "gemini", "claude", "deepseek" with "LLM" |

**Recent Activity (bottom right):**

| Current | Replace With |
|---------|--------------|
| "gemini-3-flash" | "Cloud LLM" |
| "claude-opus-4-5" | "Primary LLM" |
| Session IDs (e862f415, etc.) | Blur |

---

### 3. `v1-dashboard.jpg` (EdgePulse)

**Minimal redaction needed.** This is primarily a news/alerts dashboard.

| Location | Current | Action |
|----------|---------|--------|
| Header | "EdgePulse" | Can keep or change to "AlertPulse" |
| News headlines | Various news | Safe to keep |
| Source labels (GDELT, etc.) | Keep | These are public data sources |

---

## Generic Label Reference

Use these consistent replacements across all images:

| Specific Model/Provider | Generic Label |
|------------------------|---------------|
| claude-opus-4-5, claude-opus-4-0 | **Primary LLM** |
| gemini-*, Gemini | **Cloud LLM** or **Cloud LLM A/B** |
| gpt-4o-*, GPT-* | **Cloud LLM C** |
| deepseek-* | **Cloud LLM D** |
| llama-*, Llama | **Local LLM** or **Open Source LLM** |
| qwen*, Qwen | **Local LLM B** |
| ANTHROPIC | **Provider A** |
| OPENAI | **Provider B** |
| GOOGLE/GEMINI | **Provider C** |
| NVIDIA | **GPU Provider** |
| OPENROUTER | **Router** |
| Telegram | **Channel** |
| ollama | **Local Runtime** |
| Ezra | **Agent** or **Claw Agent** |

---

## Recommended Approach

### Option A: Blur/Pixelate (Fastest)
Use image editing to blur:
- Model names in charts
- Session IDs
- File paths
- Token counts

**Pro:** Quick. **Con:** Obviously redacted.

### Option B: Text Replacement (Cleaner)
Use image editing to replace text with generic labels.

**Pro:** Professional appearance. **Con:** More time-consuming.

### Option C: Recreate Screenshots (Best)
Create fresh screenshots with a demo/staging environment using sanitized data.

**Pro:** Perfect results. **Con:** Requires mock data setup.

---

## Priority Order

1. **v2-dashboard.jpg** — Most sensitive, must redact before any public use
2. **dashboard-main.jpg** — Redact model names and session IDs
3. **topology-*.jpg** — Skip if dashboard-main is used (they're duplicates)
4. **v1-dashboard.jpg** — Low priority, minimal redaction

---

## Notes

- Existing `-redacted.jpg` files in this folder appear to be automated/placeholder versions and should be verified
- Consider creating a `/sanitized/` subfolder for final approved versions
- Keep original files (never overwrite) for internal reference
