<p align="center">
  <img src="docs/assets/moo-moon-v1.png" alt="Moo, the golden crescent moon" width="220">
</p>

# Moo

**Moo is the moon: the general physics engine of [KheMoos](https://github.com/KheMoos).**

Moo develops our own Rust foundation for physical state, laws, materials, constraints, and solvers. Its intended real-world scope includes rigid bodies, fluids, deformable solids, thermal systems, and their interactions. [Khe](https://github.com/KheMoos/Khe), the whale, is the companion rendering engine.

## Current state

This is an early engine prototype. It contains CPU potential-derived forces and integrators, basic rigid-body rotation and constraints, GPU SPH infrastructure, and initial control/binding scaffolding. Accuracy, rendering integration, and bulk throughput remain active development work; see the repository issues for known defects.

## Build and test

Install a Rust toolchain supporting edition 2024.

```sh
cargo test --workspace --locked
cargo run -p moo --locked
```

The binary requires a compatible GPU backend. Its current demonstration loop has known initialization/stepping defects; its output is not a physics-validation benchmark. The existing automated tests exercise the CPU path.

Optional `grpc` support requires `protoc` during the build. The optional `python` feature remains binding scaffolding.

## Repository layout

- `moo/`: physics library, headless entry point, GPU kernels, and tests.
- `docs/`: design references and historical development notes.

Rendering and the interactive viewer now live in [KheMoos/Khe](https://github.com/KheMoos/Khe). The previous combined history and release tags remain here. Historical roadmaps describe the former workspace and should not be read as a current capability inventory.

## Development direction

Build reusable physics abstractions with explicit units, physical assumptions, validation cases, and measured numerical accuracy. Headless and bulk execution are core requirements. Rendering remains a separate concern exposed through a documented engine boundary.
