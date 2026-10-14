---
title: "DUET — RTL Implementation and Hardware Design Exploration"
excerpt: "RTL design, synthesis, timing closure, and design space exploration for a research accelerator targeting hybrid Mamba–Transformer inference."
collection: portfolio
permalink: /portfolio/duet/
---

DUET explores specialized hardware for the distinct compute and memory demands of LLM prefill and decode. The architecture combines configurable systolic arrays for prefill with configurable vector-unit arrays for decode, supporting both state-space and matrix multiplication operations.

## My contribution

As the third author of the paper, I primarily contributed to:

- **RTL design:** Hardware implementation for the accelerator research.
- **Synthesis:** Translating RTL into gate-level implementations and evaluating implementation characteristics.
- **Timing closure:** Refining the implementation to meet timing constraints.
- **Design space exploration (DSE):** Evaluating hardware configurations and their performance–area tradeoffs.

## Implementation and evaluation

The paper describes FP16 systolic and vector-unit arrays implemented in **SystemVerilog** and synthesized using **Synopsys Design Compiler** with a **TSMC 28 nm standard-cell library**. Its design space exploration examines array dimensions and vector-unit widths to identify configurations that balance latency, utilization, and area.

**Skills:** RTL Design · Logic Synthesis · Timing Closure · Design Space Exploration

## Related publication

Alish Kanani, Sangwan Lee, **Han Lyu**, Jiahao Lin, Jaehyun Park, and Umit Y. Ogras. *DUET: Disaggregated Hybrid Mamba-Transformer LLMs with Prefill and Decode-Specific Packages.* arXiv preprint, 2026.

[Paper](https://arxiv.org/html/2603.15530v1) · [Simulation code](https://github.com/AlishKanani/DUET) · [Publication entry]({{ '/publication/2026-03-16-duet/' | relative_url }})
