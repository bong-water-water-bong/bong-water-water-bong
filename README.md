# bong-water-water-bong — Agent HQ

> Local-first AI inference and retail automation on AMD Strix Halo (Ryzen AI MAX+ 395 / XDNA2).
> Every repo runs its own agent review stack. Every repo has a wiki an agent can read cold.

---

## Active Projects

### Inference stack

| Repo | What it is | Wiki |
|---|---|---|
| [**1bit-systems**](https://github.com/bong-water-water-bong/1bit-systems) | Strix Halo inference workbench — `1bit-proxy` union endpoint, systemd stack, FastFlowLM NPU lane, GAIA wiring | [wiki](https://github.com/bong-water-water-bong/1bit-systems/blob/main/docs/wiki/README.md) |
| [**1bit-lemonade**](https://github.com/bong-water-water-bong/1bit-lemonade) | Fork of `lemonade-sdk/lemonade` — MLX engine backend + Linux x86_64 CPU fallback | [wiki](https://github.com/bong-water-water-bong/1bit-lemonade/blob/main/docs/wiki/README.md) |
| [**lemon-asr**](https://github.com/bong-water-water-bong/lemon-asr) | OpenAI-compatible ASR server (`faster-whisper large-v3-turbo`, CPU int8) + Glasp transcript ingester | [wiki](https://github.com/bong-water-water-bong/lemon-asr/blob/main/docs/wiki/README.md) |

### Lemonade Store suite

| Repo | Department | Wiki |
|---|---|---|
| [**lemonade-store**](https://github.com/bong-water-water-bong/lemonade-store) | Umbrella — shared event envelope, department registry, store config | [wiki](https://github.com/bong-water-water-bong/lemonade-store/blob/main/docs/wiki/README.md) |
| [**lemonade-cashier**](https://github.com/bong-water-water-bong/lemonade-cashier) | Cash-only POS — cart, totals, receipts, hash-chained audit log, CIT, agents | [wiki](https://github.com/bong-water-water-bong/lemonade-cashier/blob/main/docs/wiki/README.md) |
| [**lemonade-accounting**](https://github.com/bong-water-water-bong/lemonade-accounting) | Daily close, cash reconciliation, CSV exports | [wiki](https://github.com/bong-water-water-bong/lemonade-accounting/blob/main/docs/wiki/README.md) |
| [**lemonade-security**](https://github.com/bong-water-water-bong/lemonade-security) | Event-log audit, AIBOM, supply-chain checks, OWASP LLM Top 10 findings | [wiki](https://github.com/bong-water-water-bong/lemonade-security/blob/main/docs/wiki/README.md) |

---

## Agent Review Stack

Every feature branch push runs three review passes automatically:

| Agent | When | Backed by |
|---|---|---|
| **PR-Agent** (pre-push hook) | Before every `git push` on a feature branch | `ollama/deepseek-r1:14b` local · falls back to Lemonade `Qwen3.5-4B-GGUF` |
| **Gemini Flash** (GitHub Actions) | Every PR open / sync / reopen | `gemini-2.0-flash` via `GEMINI_API_KEY` secret |
| **Claude Code Review** (GitHub Actions) | `@claude` mention in PR comment or assigned as reviewer | `claude-code-action@v1` via `ANTHROPIC_API_KEY` secret |

---

## Hardware

**AMD Ryzen AI MAX+ 395** (Strix Halo) · Ubuntu 26.04  
NPU: XDNA2 (`amdxdna`) · iGPU: Radeon 8060S · 16× Zen-5 cores · LPDDR5X

Local inference ports:

```
:13305   Lemonade Server (lemond)     — multimodal, OmniRouter, OpenAI-compat
:52625   FastFlowLM (flm)             — NPU lane, embeddings, opt-in ASR
:13306   1bit-proxy                   — union endpoint for both
:8004    lemon-asr-server             — whisper large-v3-turbo CPU int8
:11434   Ollama                       — deepseek-r1:32b / :14b, deepseek-coder
```

---

## Agent Onboarding

If you're an agent picking up work in one of these repos:

1. Read `docs/wiki/README.md` in the repo — architecture, hard rules, open threads, gotchas.
2. Check `AGENTS.md` or `CLAUDE.md` in the repo root for contributor contracts.
3. The pre-push hook runs PR-Agent before every push — don't skip it.
4. Cash-only core, local-first, owner-approval gates public side effects. See each repo's hard rules.

---

## Also shipped

- [**rocm-cpp**](https://github.com/bong-water-water-bong/rocm-cpp) — MIT HIP kernel library, multi-arch (gfx1151 + gfx1201)
- [**lemonade-vision-server**](https://github.com/bong-water-water-bong/lemonade-vision-server) — iPhone multi-modal product scanner (Qwen VLM / CLIP / ChromaDB)

---

<sub>`stamped by the architect` · Strix Halo · built in public</sub>
