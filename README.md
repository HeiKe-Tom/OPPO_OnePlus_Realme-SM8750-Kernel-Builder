# ⚡ SM8750 Kernel Lab

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=venom&height=180&text=SM8750%20KERNEL%20LAB&fontSize=42&fontColor=ffffff&color=0:0f172a,50:312e81,100:0891b2&stroke=38bdf8&strokeWidth=2&animation=fadeIn&fontAlignY=55" width="100%" alt="SM8750 Kernel Lab" />

### OPPO / OnePlus / realme · Android Kernel CI/CD

**A cloud-first automated Linux 6.6 kernel build system for Qualcomm SM8750 and selected MT6991 targets.**

[![Build](https://img.shields.io/github/actions/workflow/status/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml?branch=main&style=for-the-badge&logo=github-actions&logoColor=white&label=CI%20BUILD)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml)
[![Release](https://img.shields.io/github/v/release/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge&logo=github&label=LATEST%20RELEASE)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/releases/latest)
[![Kernel](https://img.shields.io/badge/Linux%20Kernel-6.6.89-2563eb?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions)
[![Stars](https://img.shields.io/github/stars/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge&logo=github)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/stargazers)
[![License](https://img.shields.io/github/license/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge)](LICENSE)

**[🚀 Run Cloud Build](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml)** · **[📦 Releases](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/releases)** · **[🐛 Issues](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/issues)**

</div>

---

## 🖥️ System Status

```text
┌──────────────────────────────────────────────────────────┐
│  $ ./kernel-builder                                      │
│                                                          │
│  [✓] Platform      : Qualcomm SM8750 / MT6991            │
│  [✓] Kernel        : Linux 6.6.x                         │
│  [✓] Build System  : GitHub Actions                      │
│  [✓] Toolchain     : LLVM / Clang                        │
│  [✓] Cache         : ccache                              │
│  [✓] Output        : Image / Modules / AnyKernel3        │
│                                                          │
│  > Cloud build environment ready...                     │
└──────────────────────────────────────────────────────────┘
```

> **Cloud-first:** no local Linux build environment is required for the normal workflow. Select the target and feature set in **Actions → Run workflow**, then download the generated artifacts or Release package.

---

## 🚀 Cloud Kernel Builder

### 1. Open Actions

Go to **Actions → 🚀 OPPO_OnePlus_Realme SM8750 Kernel Builder → Run workflow**.

### 2. Select your build

Choose the kernel target, KernelSU implementation and optional kernel features.

### 3. Start CI

GitHub Actions prepares the build environment, applies patches, compiles the kernel and packages the output.

### 4. Download

Use the generated **Artifacts** or the corresponding **Release** package.

> This project is designed so users do not need to install LLVM, Android build dependencies, ccache or a complete kernel build environment locally just to perform a normal build.

---

## 🏗️ Build Pipeline

```text
┌──────────────────┐
│ GitHub Actions   │
│ workflow_dispatch│
└────────┬─────────┘
         ↓
┌──────────────────┐
│ Kernel Target    │
│ Linux 6.6.x      │
└────────┬─────────┘
         ↓
┌──────────────────┐
│ Patch Engine     │
│ KSU / SUSFS /    │
│ KPM / ZRAM / IO  │
└────────┬─────────┘
         ↓
┌──────────────────┐
│ LLVM / Clang     │
│ ccache            │
└────────┬─────────┘
         ↓
┌──────────────────┐
│ Kernel Image     │
│ Modules / DTB    │
└────────┬─────────┘
         ↓
┌──────────────────┐
│ AnyKernel3 /     │
│ Release Artifact │
└──────────────────┘
```

---

## 🧩 Feature Matrix

| Component | Status | Configuration |
|---|:---:|---|
| Linux Kernel 6.6 | 🟢 | Multiple target versions |
| KernelSU | 🟢 | ReSukiSU / SukiSU / KSU Next / KSU / None |
| SUSFS | 🟢 | Optional |
| KPM / KpatchNext | 🟢 | Optional |
| LZ4 1.10.0 | 🟢 | Optional |
| ZSTD 1.5.7 | 🟢 | Optional |
| LZ4KD | 🟢 | Optional |
| BBR | 🟢 | Off / algorithm only / default |
| DroidSpaces | 🟢 | Off / standard / extend |
| Advanced Network | 🟢 | ipset / iptables support |
| ADIOS | 🟢 | Optional |
| Re-Kernel | 🟢 | Optional |
| Baseband Guard | 🟢 | Optional |
| ccache | 🟢 | Build cache / debug support |

---

## 📦 Kernel Targets

| Kernel Target | Platform | Role | Status |
|---|---|---|:---:|
| `6.6.30` | SM8750 | Legacy target | 🟢 |
| `6.6.50` | MT6991 / MTK | MTK target | 🟢 |
| `6.6.56` | SM8750 | Build target | 🟢 |
| `6.6.57` | SM8750 | Build target | 🟢 |
| `6.6.66` | SM8750 | Build target | 🟢 |
| `6.6.89` | SM8750 | **Workflow default** | 🟢 |
| `6.6.89 MTK` | MT6991 / MTK | MTK target | 🟢 |
| `6.6.118` | SM8750 | Newer 6.6 target | 🟢 |

> The current Workflow default is **6.6.89**. The README intentionally follows the actual Workflow default instead of displaying 6.6.118 as the default build target.

---

## ⚙️ Workflow Configuration

| Input | Default | Description |
|---|---|---|
| `kernel_target` | `6.6.89` | Kernel version / target |
| `ksu_type` | `resukisu` | KernelSU implementation |
| `susfs_enable` | `true` | Enable SUSFS |
| `kpm_enable` | `false` | Enable KPM / KpatchNext |
| `lz4_enable` | `true` | LZ4 / ZSTD patches |
| `lz4kd_enable` | `false` | Enable LZ4KD |
| `bbr_enable` | `false` | BBR configuration |
| `droidspaces_enable` | `false` | DroidSpaces mode |
| `better_net` | `false` | Advanced network support |
| `adios_enable` | `true` | ADIOS IO scheduler |
| `rekernel_enable` | `false` | Re-Kernel support |
| `baseband_guard` | `true` | Baseband protection |
| `ccache_update` | `false` | Update repository ccache |
| `ccache_debug` | `false` | Upload ccache debug logs |
| `kernel_suffix` | `android15-8-g29d86c5fc9dd-abogki428889875-4k` | Custom kernel suffix |

---

## 📱 Platform Matrix

| SoC | Vendor / Platform | Android | Kernel | Status |
|---|---|---|---|:---:|
| **SM8750** | OPPO | 15 / 16 | 6.6.x | 🟢 |
| **SM8750** | OnePlus | 15 / 16 | 6.6.x | 🟢 |
| **SM8750** | realme | 15 / 16 | 6.6.x | 🟢 |
| **MT6991** | MediaTek targets | 15 / 16 | 6.6.x | 🟡 |

### ⚠️ Platform boundary

```text
SM8750 ≠ MT6991
```

Do **not** cross-flash between different SoC platforms. Platform compatibility also depends on the boot chain, DTB, vendor_dlkm, KMI/ABI, vendor drivers, Android version and OEM-specific integration.

Recommended device-side checks:

```bash
getprop ro.soc.model
getprop ro.board.platform
uname -a
getprop ro.build.version.release
getprop ro.boot.slot_suffix
```

---

## 📊 Build Status

| Workflow | Purpose |
|---|---|
| 🚀 **SM8750 Kernel Builder** | Main kernel CI / packaging |
| 🧹 **Repository Cleaner** | Repository cleanup |
| 🗑️ **ccache Cleaner** | ccache maintenance |

[![Main CI](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml/badge.svg?branch=main)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml)
[![Repository Cleanup](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/clean_workflow.yml/badge.svg?branch=main)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/clean_workflow.yml)
[![ccache Cleaner](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/cleaner.yml/badge.svg?branch=main)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/cleaner.yml)

---

## 📦 Release & Artifacts

GitHub Actions can publish build artifacts and Release packages containing the generated kernel output, including **AnyKernel3 ZIP** packages when enabled by the current build flow.

**Important:** always read the individual Release notes and build metadata. The README describes the builder capabilities; it does not guarantee that every Release uses every optional feature.

---

## 🧪 Verification

Before flashing, inspect the resulting kernel where applicable:

```bash
file Image
strings Image | grep -E "Linux version|android"
```

On-device verification:

```bash
uname -a
getprop ro.soc.model
getprop ro.board.platform
getprop ro.boot.slot_suffix
getprop ro.build.version.release
```

If KernelSU, SUSFS, KPM or other optional features are selected, verify that the feature is present in the final Image rather than assuming that a CI input alone proves integration.

---

## 🛡️ Safety / Recovery

Third-party kernels can fail because of KMI/ABI differences, DTB mismatches, vendor_dlkm differences, boot header differences or OEM-specific drivers.

Before flashing, keep a complete rollback path. At minimum, consider backing up the device's corresponding:

- `boot.img`
- `vendor_boot.img`
- `init_boot.img` when present
- `dtbo.img`
- `vbmeta.img`
- matching official OTA / recovery package

**Do not treat Baseband Guard as a complete anti-brick solution.** Critical partitions such as `modem`, `efs`, `persist`, `super` and `boot` still require proper backups and recovery planning.

---

## 📂 Repository Layout

```text
.
├── .github/
│   └── workflows/
│       ├── OPPO_OnePlus_Realme SM8750 Kernel Builder.yml
│       ├── build-test.yml
│       ├── clean_workflow.yml
│       └── cleaner.yml
├── droidspaces_patch/
├── lib/
├── local/
├── other_patch/
├── zram_patch/
├── zram.zip
└── README.md
```

---

## 🔧 Local Build

```bash
git clone https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder.git
cd OPPO_OnePlus_Realme-SM8750-Kernel-Builder
```

The exact local entry points follow the current contents of `local/` and `lib/`. For most users, GitHub Actions is recommended to reduce differences in LLVM, dependencies, ccache and environment configuration.

---

## 🤝 Contributing

Contributions are welcome in the following areas:

- 🐛 Build failure reports
- 📱 New device / target support
- 🧩 New kernel version support
- 🔧 Patch improvements
- ⚡ CI performance optimization
- 🛠️ Toolchain improvements
- 🔐 KernelSU / SUSFS integration

When reporting a build issue, include:

```text
Device:
SoC:
ROM:
Android:
Kernel:
Boot version:
KernelSU:
SUSFS:
Workflow:
Complete error log:
```

---

## 🙏 Credits

This project integrates or builds upon work from the Android kernel community, including:

- ReSukiSU
- SukiSU Ultra
- KernelSU Next
- KernelSU
- susfs4ksu
- SukiSU_patch
- WildKernels kernel patches
- ADIOS
- Other upstream kernel / Android community projects used by the build pipeline

Please refer to the corresponding upstream repositories and licenses for their individual components.

---

<div align="center">

### ⚡ HeiKe-Tom Kernel Lab

`Android Kernel` · `KernelSU` · `SUSFS` · `GitHub Actions` · `SM8750` · `MT6991` · `Linux 6.6`

**Built in the cloud. Tested on real devices.**

[![GitHub](https://img.shields.io/badge/GitHub-HeiKe--Tom-181717?style=for-the-badge&logo=github)](https://github.com/HeiKe-Tom)

</div>
