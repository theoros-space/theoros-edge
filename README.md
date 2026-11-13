<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/banners/edge-dark.png">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/banners/edge-light.png">
  <img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/banners/edge-light.png" width="100%" alt="theoros-edge">
</picture>

<p><a href="LICENSE"><img src="https://img.shields.io/badge/license-source--available%201.0-FF4B1F?style=flat-square&labelColor=11151C" alt="license: source-available 1.0"></a> <img src="https://img.shields.io/badge/status-pre--release-8B929D?style=flat-square&labelColor=11151C" alt="status: pre-release"> <a href="https://github.com/theoros-space"><img src="https://img.shields.io/badge/part-02%20of%2006-3E7BFA?style=flat-square&labelColor=11151C" alt="part: 02 of 06"></a></p>

> [!NOTE]
> **Status:** Pre-release. The repository is public so partners and reviewers can follow the work. Source code lands here from December 2026.

## Overview

The code that runs on the satellite. One portable C runtime that runs on any
flight computer, plus exports for the AI processors flying today. The
portable runtime is the reference: every other target must reproduce its
outputs bit for bit on the verification set.

## Where it fits

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/diagrams/flow-dark.png">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/diagrams/flow-light.png">
  <img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/diagrams/flow-light.png" width="100%" alt="How Theoros works: sensor, onboard inference, answers, ground, compiler, signed update">
</picture>

| | Repository | Role |
|:-:|---|---|
| `01` | [theoros-models](https://github.com/theoros-space/theoros-models) | Multi-task model, training and the ground compiler |
| `02` | **theoros-edge** | Onboard int8 runtime and flight targets |
| `03` | [theoros-delivery](https://github.com/theoros-space/theoros-delivery) | Signed model packages and over-the-air updates |
| `04` | [theoros-ground](https://github.com/theoros-space/theoros-ground) | Customer API, mission dashboard and result tracking |
| `05` | [theoros-bench](https://github.com/theoros-space/theoros-bench) | Open benchmark for onboard Earth observation AI |
| `06` | [theoros-docs](https://github.com/theoros-space/theoros-docs) | Technical documentation and flight documents |

## Flight targets

| Target | Hardware class | Toolchain |
|---|---|---|
| Portable C int8 | Any flight computer, microcontrollers | C99, no dynamic memory |
| OpenVINO | Intel Movidius Myriad X | OpenVINO |
| TensorRT | NVIDIA Jetson Orin | TensorRT |
| Vitis AI | AMD Xilinx FPGA with DPU | Vitis AI |

## Design rules

- **Static memory.** Every buffer is sized at compile time; nothing is allocated in flight.
- **Integrity first.** A model is loaded only after its signature and checksum verify.
- **Deterministic.** Same input, same output, on every target and every run.
- **Small interface.** One C header, documented in the interface control document.

## Repository layout

Planned structure. Directories appear as the code lands.

```text
include/theoros/     public C API
src/                 int8 kernels, model loader, integrity checks
targets/             openvino/, tensorrt/, vitis-ai/
docs/                interface control document, requirements, resource budget
tests/               kernel tests and hardware-in-the-loop scripts
```

## Requirements

Every requirement lives in [docs/REQUIREMENTS.md](docs/REQUIREMENTS.md) with
the prefix `EDGE-REQ`. Each one names how it is verified (test, analysis or
inspection), and every pull request that changes behaviour cites the
requirement it serves.

## Contributing

Read the [contributing guide](https://github.com/theoros-space/.github/blob/main/CONTRIBUTING.md)
before opening a pull request. Outside contributions need a signed
[Contributor License Agreement](https://github.com/theoros-space/.github/blob/main/CLA.md).
Report vulnerabilities privately as described in the
[security policy](https://github.com/theoros-space/.github/blob/main/SECURITY.md), never in a public issue.

## License

Source-available under the [Theoros Source-Available License 1.0](LICENSE).
You may read and evaluate this repository. Production use, modification,
redistribution and training competing models need a written license from
Theoros: licensing@theoros.space. See [which license applies where](https://github.com/theoros-space/.github/blob/main/LICENSING.md).

---

<p align="center">
  <a href="https://github.com/theoros-space"><picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/logo/svg/mark-paper.svg">
    <img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/logo/svg/mark-ink.svg" width="28" alt="Theoros">
  </picture></a>
  <br>
  <sub>Theoros &nbsp;·&nbsp; Onboard AI for Earth observation &nbsp;·&nbsp; Baku and Helsinki &nbsp;·&nbsp; <a href="https://theoros.space">theoros.space</a></sub>
</p>
