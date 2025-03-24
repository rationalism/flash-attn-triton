# Flash Attention Triton

This repository provides a Triton-based implementation of the Flash Attention algorithm with a Flash Attention 2 compatible API. It allows for a drop-in replacement of the original Flash Attention 2 package for supported functionality.

## Installation

You can install the package directly from GitHub:

```bash
pip install git+https://github.com/rationalism/flash-attn-triton.git
```

Or from PyPI:

```bash
pip install flash-attn-triton
```

## Requirements

- PyTorch 2.6 or later
- Triton 3.2 or later
- CUDA-compatible GPU (compute capability 5.0+)

## Usage

The API is designed to be compatible with Flash Attention 2. You can use it in the same way:

```python
from flash_attn_triton import flash_attn_func, flash_attn_qkvpacked_func, FlashAttention

# Basic usage
out = flash_attn_func(q, k, v, causal=True)

# Packed QKV
out = flash_attn_qkvpacked_func(qkv, causal=True)

# Module interface
flash_attn = FlashAttention()
out = flash_attn(q, k, v, causal=True)
```

## Currently Supported Features

- Basic attention mechanism
- Causal masking
- Softmax scaling
- Basic MQA/GQA support (via tensor repetition)

## Limitations

This implementation does not currently support:

- Dropout
- Attention bias
- Sliding window attention
- ALiBi
- Rotary embeddings
- KV caching with in-place updates
- Paged KV cache
- Softcapping
- Deterministic backward pass

## Acknowledgements

This implementation is based on the Triton attention implementation from the original Flash Attention 2 repository by TriDao and the Triton tutorial on fused attention.

## License

This project is licensed under the BSD 3-Clause License - see the LICENSE file for details.
