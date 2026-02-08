# 🧠 ComfyUI – Qwen TTS Setup Guide

This document explains how to deploy **Qwen TTS** inside **ComfyUI**, the issues encountered during setup, and the final working solution.

---

## 🔗 Workflow / Repository
ComfyUI-Qwen-TTS  
https://github.com/flybirdxx/ComfyUI-Qwen-TTS

---

## 🧾 Overview
An attempt was made to deploy **Qwen TTS** using the above workflow inside **ComfyUI**.  
The setup **does not work correctly out of the box** and fails due to dependency-related issues.

---

## ❌ Error Encountered

During execution, the following error occurs:

```text
'Qwen3TTSTalkerConfig' object has no attribute 'pad_token_id'
```

---

## 🧩 Root Cause
The error is caused by **incorrect or missing Python dependencies**.

- Required packages are not fully installed by default  
- Some dependencies are installed in conflicting versions  
- The error message is misleading — the issue is **environment-related**, not model-related

---

## 🛠️ Manual Installation Attempt

### Step 1: Install Required Dependencies
Run the following command from the ComfyUI root directory:

```powershell
.\python_embeded\python.exe -m pip install -r .\ComfyUI\custom_nodes\ComfyUI-Qwen-TTS\requirements.txt
```

### Step 2: Handle Conflicting Packages
After installing the requirements:
- Existing packages may conflict with required versions
- Conflicts must be manually identified and removed
- The environment can easily become unstable

**Result:** ❌ Unreliable and time-consuming

---

## ✅ Final Working Solution (Recommended)

The issue was fully resolved by using **Pinokio**.

### Why Pinokio Works
Pinokio automatically handles:
- Python environment setup  
- Dependency installation  
- Version conflict resolution  

After installing via Pinokio:
- Qwen TTS runs correctly inside ComfyUI  
- No `pad_token_id` error  
- Stable and reproducible setup

---

## 🧠 Lessons Learned
- The ComfyUI-Qwen-TTS workflow is **highly sensitive to dependency versions**
- Manual installation can easily break the environment
- Error messages may not indicate the true cause
- **Pinokio is the recommended approach** for a clean setup

---

## 📌 Status
- Setup: ✅ Working  
- Manual install: ⚠️ Not recommended  
- Recommended method: ⭐ Pinokio
