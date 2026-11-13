<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/logo/svg/mark-paper.svg">
  <img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/logo/svg/mark-ink.svg" width="44" align="right" alt="Theoros">
</picture>

# theoros-edge

**02  Onboard int8 runtime and flight targets.** Part of the [Theoros](https://github.com/theoros-space) onboard AI product.

[![License: Theoros Source-Available 1.0](https://img.shields.io/badge/license-source--available-FF4B1F)](LICENSE)

> **Status: pre-release.** This repository is public so partners can follow our work. Source code lands here from December 2026.

## What it is

The code that runs on the satellite. One portable C runtime that runs
anywhere, plus exports for the AI processors flying today.

| Target | Hardware class | Toolchain |
|---|---|---|
| Portable C int8 | Any flight computer, microcontrollers | C99, no dynamic memory |
| OpenVINO | Intel Movidius Myriad X | OpenVINO |
| TensorRT | NVIDIA Jetson Orin | TensorRT |
| Vitis AI | AMD Xilinx FPGA with DPU | Vitis AI |

The portable C runtime is the reference: every other target must reproduce
its outputs bit for bit on the verification set.

## Planned layout

```
include/theoros/     public C API
src/                 int8 kernels, model loader, integrity checks
targets/             openvino/, tensorrt/, vitis-ai/
docs/                ICD, requirements, resource budget
tests/               kernel tests and hardware-in-the-loop scripts
```

## Requirements

Requirements are listed in [docs/REQUIREMENTS.md](docs/REQUIREMENTS.md) with
the prefix `EDGE-REQ`. Every requirement is verified by a test, an
analysis or an inspection, and referenced in the pull request that changes it.

## Contributing

See the organisation [contributing guide](https://github.com/theoros-space/.github/blob/main/CONTRIBUTING.md).
Outside contributions need a signed [CLA](https://github.com/theoros-space/.github/blob/main/CLA.md).

## License

Source-available under the [Theoros Source-Available License 1.0](LICENSE).
You may read and evaluate it; any use, copy or deployment needs a written
license from Theoros. Contact licensing@theoros.space.
