# hi — I'm the architect behind [1bit.systems](https://1bit.systems/)

Local, ternary-quantized AI inference on AMD Strix Halo. Zero cloud, zero Python at runtime.

## what I'm building

[**1bit-systems**](https://github.com/bong-water-water-bong/1bit-systems) — C++ HIP kernels + Rust orchestration for a 2B/3.9B BitNet stack native to gfx1151 + gfx1201. OpenAI-compatible at `:8180`, glass-walled, built in public.

- Ternary GEMV kernel @ **92%** of LPDDR5 peak bandwidth
- Split-KV Flash-Decoding attention — **6.78x** over single-block
- Wikitext-103 perplexity **9.1805** (gen-1 baseline 9.1607)
- 17-specialist agent registry · 4 LLM-backed live in Discord
- No hipBLAS · no Python · no vendor lock-in

## also shipped

- [**rocm-cpp**](https://github.com/bong-water-water-bong/rocm-cpp) — MIT-licensed HIP kernel library, multi-arch (gfx1151 + gfx1201)
- [**llamacpp-rocm**](https://github.com/bong-water-water-bong/llamacpp-rocm) — ROCm 7.x bootstrap for Strix Halo
- [**sd.cpp**](https://github.com/bong-water-water-bong/sd.cpp) — native-HIP SDXL port

## support

If the stack saves you GPU rent or teaches you something you couldn't find elsewhere, sponsor the work. One sponsor at $10/mo covers ~3h of H200 training time. Ten covers one full 10B-token training run per month.

- [GitHub Sponsors](https://github.com/sponsors/bong-water-water-bong) (pending)
- [Patreon](https://www.patreon.com/1bitsystems)
- [Discord](https://1bit.systems/)

---

<sub>*"I know kung fu."*  —  `stamped by the architect`</sub>
