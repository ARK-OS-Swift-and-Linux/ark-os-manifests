# ARK-OS Declarative System Manifests

## Overview

The `manifests/` repository houses the declarative configuration files, architecture target profiles, component registries, and cryptographic source lockfiles that define the ARK-OS build matrix.

All manifests are version-controlled, auditable, and formatted in standard TOML.

---

## Directory Organization

- `sources.lock.toml` - Immutable record of all external source dependencies (e.g., upstream Linux kernel source releases) with verified cryptographic SHA-256 checksums, download URLs, and release categories.
- `components.toml` - Canonical registry of first-party system components, their filesystem locations, implementation languages, build roles, and execution artifacts.
- `targets/` - Platform- and architecture-specific build manifests and kernel configurations:
  - `targets/x86_64.toml` - Target profile for x86_64 QEMU/KVM virtual bring-up, toolchain requirements, and emulator execution parameters.
  - `targets/x86_64.defconfig` - Minimal Linux kernel configuration baseline tailored for initial RAM-only bring-up.
  - `targets/arm64.toml` - Target profile for 64-bit ARM architectures (future milestone).

---

## Invariants and Maintenance Rules

- **Deterministic Dependencies:** Every external source archive referenced by ARK-OS must have an exact cryptographic SHA-256 checksum recorded in `sources.lock.toml` before use. Checksums must never be estimated or omitted.
- **Accurate Toolchain Records:** Target manifests must accurately reflect tested compiler requirements and toolchain limitations without inventing unverified dependencies.

---

## License

This repository is licensed under the Apache License, Version 2.0. See [LICENSE](file:///home/aarav/repo/arkos/manifests/LICENSE) for the full license text.
