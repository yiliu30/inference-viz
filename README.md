# Inference Viz

**Understand AI inference, one interactive visualization at a time.**

A collection of interactive HTML visualizations exploring **low-bit quantization, efficient attention, GPU architecture, kernel optimization, memory systems, and multimodal inference**.

**[Browse the live gallery](https://yiliu30.github.io/viz/)** · **[GitHub profile](https://github.com/yiliu30)**

## Featured demos

| Visualization | Open live demo |
| --- | --- |
| BlockSelector: subblock Top-K | [Interactive demo](https://yiliu30.github.io/viz/blockselector_subblock_topk_interactive.html) |
| RainFusion MXFP8 attention | [Interactive demo](https://yiliu30.github.io/viz/rainfusion_mxfp8_interactive.html) |
| Tiny GPU execution trace | [Interactive demo](https://yiliu30.github.io/viz/tiny_gpu_trace_explorer%20%282%29.html) |
| Attention error lab (TRIAGE) | [Interactive demo](https://yiliu30.github.io/viz/triage_attention_error_lab.html) |

## Repository layout

- `viz/` — standalone interactive HTML pages (source for the live gallery).
- `data/viz_tags.json` — topical tags used by the gallery.
- `docs/` — publishing and migration notes.

## Use locally

Open an HTML page in `viz/` in a browser. Some visualizations may use third-party browser libraries loaded from CDNs.

## Publishing

The established public URL is **https://yiliu30.github.io/viz/**. Its Hugo site lives at [yiliu30/yiliu30.github.io](https://github.com/yiliu30/yiliu30.github.io).

This repository collects visualization sources separately from the rest of the blog. See [migration notes](docs/MIGRATION.md) for the sync and deployment setup.

## Topics

Quantization (INT4, FP8, MXFP4/MXFP8, NVFP4), attention and block sparsity, GPU kernels and profiling, model architecture, and KV-cache / memory behavior.

Created and maintained by [Yi Liu](https://github.com/yiliu30).
