# 🎙️ Local AI Voice Clone

> *Because your voice should be everywhere*

---

## 🧠 ComfyUI – Qwen TTS Setup Guide

This document explains how to deploy **Qwen TTS** inside **ComfyUI**, the issues encountered during setup, and the final working solution.

---

## 🔗 Workflow / Repository

| | |
|---|---|
| **Name** | ComfyUI-Qwen-TTS |
| **URL** | https://github.com/flybirdxx/ComfyUI-Qwen-TTS |
| **Status** | ⚠️ Needs Pinokio |

---

## 🧾 Overview

> [!WARNING] Manual Setup Issues
> An attempt was made to deploy **Qwen TTS** using the above workflow inside **ComfyUI**.  
> The setup **does not work correctly out of the box** and fails due to dependency-related issues.

---

## ❌ Error Encountered

During execution, the following error occurs:

```
'Qwen3TTSTalkerConfig' object has no attribute 'pad_token_id'
```

---

## 🧩 Root Cause

The error is caused by **incorrect or missing Python dependencies**.

| Issue | Impact |
|-------|--------|
| Required packages not fully installed | Missing functionality |
| Conflicting versions | Runtime errors |
| Misleading error message | Hard to debug |

> [!INFO] The issue is **environment-related**, not model-related

---

## 🛠️ Manual Installation Attempt

### Step 1: Install Required Dependencies

```powershell
.\python_embeded\python.exe -m pip install -r .\ComfyUI\custom_nodes\ComfyUI-Qwen-TTS\requirements.txt
```

### Step 2: Handle Conflicting Packages

| Problem | Solution |
|---------|----------|
| Existing packages conflict | Manual identification |
| Version mismatches | Remove and reinstall |
| Unstable environment | Start fresh |

**Result:** ❌ Unreliable and time-consuming

---

## ✅ Final Working Solution (Recommended)

> [!SUCCESS] Use Pinokio!
> The issue was fully resolved by using **[Pinokio](https://pinokio.computer/)**.

### Why Pinokio Works

| Feature | Benefit |
|---------|---------|
| ✅ Python environment setup | Automatic |
| ✅ Dependency installation | Automatic |
| ✅ Version conflict resolution | Automatic |
| ✅ Stable setup | Guaranteed |

**After installing via Pinokio:**
- ✅ Qwen TTS runs correctly inside ComfyUI
- ✅ No `pad_token_id` error
- ✅ Stable and reproducible setup

---

## 🧠 Lessons Learned

| Lesson | Takeaway |
|--------|----------|
| ⚠️ Dependency sensitivity | ComfyUI-Qwen-TTS is highly sensitive to versions |
| ❌ Manual install | Can easily break the environment |
| 🔍 Error messages | May not indicate the true cause |
| ⭐ **Recommended method** | **Pinokio** |

---

## 📌 Status Overview

| Method | Status |
|--------|:------:|
| Setup | ✅ Working |
| Manual install | ⚠️ Not recommended |
| Pinokio method | ⭐ **Recommended** |

---

## 🔗 Related

- [[Research - 🧠 ComfyUI – Qwen TTS Setup Guide]]
- [[ComfyUI]] — Main ComfyUI workflows
- [[Tasks & Inbox]] — Active projects

---

*Documented by Lilly* 🤖💕
