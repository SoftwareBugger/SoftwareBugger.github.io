---
title: "ProType NPU — FPGA LLM Inference"
excerpt: "A custom NPU on KR260 running Granite 4.0 350M through a native C chat runtime, with tensor and vector engines and measured inference profiling."
collection: portfolio
permalink: /portfolio/npu/
---

ProType NPU is my hardware project for neural network inference on the KR260 FPGA platform. The local demo runs Granite 4.0 350M using a custom NPU and a native C chat runtime.

## Hardware and software architecture

The documented board release runs all 28 decoder layers and the vocabulary head on the FPGA at 200 MHz. The ARM host handles tokenization, embedding lookup and scaling, greedy sampling, and the HTTP chat service.

- **Instruction-driven control:** A MiniISA frontend sequences tensor, vector, and DMA operations.
- **Tensor engine:** Quantized W8A16 matrix–vector computation and FP32 attention QK/PV operations.
- **Vector engine:** RMSNorm, softmax, rotary position embeddings (RoPE), and activation operations.
- **Memory and host integration:** Banked local memory, AXI interfaces, DMA, and Linux device control.
- **Software tools:** Graph compilation, model preparation, numerical reference models, and runtime packaging.

## Local chat demonstration

<figure>
  <a href="{{ '/images/projects/npu-chat-demo.png' | relative_url }}">
    <img src="{{ '/images/projects/npu-chat-demo.png' | relative_url }}" alt="Local Granite 4.0 350M FPGA chat demo responding to a Verilog full-adder prompt, alongside inference latency and throughput measurements" loading="lazy" />
  </a>
  <figcaption>Local FPGA chat demo with request profiling. Click the image to view it at full resolution.</figcaption>
</figure>

The screenshot shows a request asking the model to write a Verilog full adder, with 38 prompt tokens and 92 output tokens. The generated text illustrates model inference; it has not been presented as verified RTL.

| Measurement | Shown request |
| --- | ---: |
| Server first-token latency | 5,812.9 ms |
| Decode throughput | 3.64 tokens/s |
| Complete response time | 30,782.5 ms |
| Browser first-token latency | 5,817.4 ms |

These are measurements from this individual demo request. Throughput and latency vary with prompt length and context.

## Verification

The retained project reports document full-NPU functional regression coverage for DMA, quantized computation, attention, vector operations, fault handling, and recovery. Compact compiled decoder-layer tests compare outputs and KV state against numerical references. Board-release checks separately cover tokenizer parity and captured FPGA tensors.

## Availability

The demo runs locally. Source code has not yet been published on GitHub.

**Skills:** NPU Architecture · SystemVerilog · Quantized Inference · FPGA Integration · AXI/DMA · Linux Runtime · Numerical Verification
