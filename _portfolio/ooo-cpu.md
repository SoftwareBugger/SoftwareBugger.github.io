---
title: "HanOoO — Out-of-Order RV32I RISC-V SoC"
excerpt: "A from-scratch out-of-order RISC-V processor with register renaming, precise commit, and an FPGA demo running bare-metal C firmware."
collection: portfolio
permalink: /portfolio/ooo-cpu/
---

HanOoO is my from-scratch RV32I out-of-order processor project, integrated into a small SoC that runs bare-metal C firmware on FPGA. The project connects processor microarchitecture with peripherals and an interactive application.

## Core architecture

- Out-of-order execution with in-order commit.
- Register renaming and a physical register file.
- Reservation stations with wakeup and instruction selection.
- A reorder buffer for precise architectural state and branch recovery.
- Conservative load handling and stores issued at commit for memory correctness.

[![HanOoO core architecture]({{ '/images/projects/hanooo-architecture.png' | relative_url }})]({{ '/images/projects/hanooo-architecture.png' | relative_url }})

## From CPU to FPGA demo

The SoC integrates memory-mapped UART and SPI peripherals, a boot ROM, and a bare-metal firmware memory layout. Its Dino runner game accepts UART input and renders graphics on an SPI OLED display, demonstrating firmware execution and peripheral interaction on the processor.

<figure>
  <img src="{{ '/images/projects/hanooo-fpga.jpg' | relative_url }}" alt="HanOoO FPGA setup with an SPI OLED displaying the Dino runner game" loading="lazy" style="max-height: 600px; width: auto; max-width: 100%;" />
  <figcaption>FPGA demonstration of the processor, peripherals, and bare-metal game firmware.</figcaption>
</figure>

This is an educational microarchitecture project focused on correctness and hardware/software integration.

**Skills:** CPU Microarchitecture · Register Renaming · RTL Design · FPGA Integration · Bare-Metal Firmware

[Source code and documentation](https://github.com/SoftwareBugger/Han_OoO)
