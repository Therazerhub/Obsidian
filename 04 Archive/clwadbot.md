# Early OpenClaw Setup Notes

Early scratchpad from initial setup attempts. Historical reference — see [[Projects/Lilly Setup]] for the working configuration.

---

## Decisions Made

| Decision | Options Considered | Final Choice |
|----------|-------------------|--------------|
| **Hosting** | AWS vs Phone | **AWS** (more reliable, 24/7) |
| **AI Provider** | Copilot vs Azure Student ID | **NVIDIA API** (found later) |

---

## Quick Access Commands

```bash
# SSH to VPS
ssh -i "openclaw.pem" ubuntu@ec2-56-228-35-215.eu-north-1.compute.amazonaws.com

# Port forward for local gateway access
ssh -i openclaw.pem -N -L 18789:127.0.0.1:18789 ubuntu@56.228.35.215
```

---

## Integration Attempts

**Goal:** Integrate Clawbot with NVIDIA Kimi 2.5

**Status:** ✅ Completed via OpenClaw + NVIDIA API integration

**Final Setup:**
- Primary: `ollama/kimi-k2.5:cloud` (local)
- Fallback: `nvidia/moonshotai/kimi-k2.5` (cloud)

---

## Security Note

Original notes contained exposed API tokens and gateway credentials. These have been:
1. Moved to `_secure/` folder
2. Regenerated/revoked where applicable
3. Referenced via environment variables in working configs

---

*Historical doc — 2026-02-07 to 2026-02-08*
