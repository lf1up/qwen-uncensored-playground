# Qwen 3.5 35B-A3B Uncensored Playground

A Jupyter notebook that runs [Qwen3.5-35B-A3B-Uncensored](https://huggingface.co/HauhauCS/Qwen3.5-35B-A3B-Uncensored-HauhauCS-Aggressive) (Q6_K, ~28 GB) locally via [llama.cpp](https://github.com/ggml-org/llama.cpp) and serves a Gradio chat UI with streaming and adjustable parameters.

## Requirements

- **GPU**: NVIDIA with CUDA 12.8+ and at least 32 GB VRAM (tested on A100 80GB)
- **Python**: 3.12
- **Platform**: Linux x86_64

## Quick start with Modal (recommended)

The fastest way to get running — no local GPU needed:

1. Create a free account at [modal.com](https://modal.com)
2. Go to [Notebooks](https://modal.com/notebooks) and upload `qwen_uncensored.ipynb`
3. In the sidebar, set the kernel GPU to **A100 80GB** (or any GPU with 32+ GB VRAM)
4. Run all cells — the model downloads, loads onto the GPU, and Gradio gives you a public chat URL

The whole setup takes about 5 minutes. You only pay for the seconds the kernel is running.

## Quick start (local)

Open `qwen_uncensored.ipynb` and run all cells in order:

| Cell | What it does |
|------|-------------|
| 0 | Installs [JamePeng's llama-cpp-python fork](https://github.com/JamePeng/llama-cpp-python) (pre-built CUDA 12.8 wheel), Gradio, and NVIDIA runtime libs |
| 1 | Downloads the Q6_K GGUF from HuggingFace (cached after first run) |
| 2 | Loads the model onto the GPU |
| 3 | Launches the Gradio chat interface |

The Gradio UI provides a shareable public URL via `share=True`.

## Default parameters

Defaults follow the [official Qwen3.5 recommended settings](https://huggingface.co/Qwen/Qwen3.5-35B-A3B) for thinking mode (general tasks):

| Parameter | Default |
|-----------|---------|
| Temperature | 1.0 |
| Top-p | 0.95 |
| Top-k | 20 |
| Max tokens | 8192 |
| Repeat penalty | 1.0 |

All parameters are adjustable via sliders in the sidebar.

## Model

- **Base**: [Qwen/Qwen3.5-35B-A3B](https://huggingface.co/Qwen/Qwen3.5-35B-A3B) — 35B total params, ~3B active per forward pass (MoE)
- **Uncensored by**: [HauhauCS](https://huggingface.co/HauhauCS/Qwen3.5-35B-A3B-Uncensored-HauhauCS-Aggressive) (Aggressive variant, 0/465 refusals)
- **Quantization**: Q6_K (6.58 BPW, imatrix)

## License

MIT
