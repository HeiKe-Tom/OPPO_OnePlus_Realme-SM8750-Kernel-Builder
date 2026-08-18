# OPPO / OnePlus / realme SM8750 Kernel Builder

<div align="center">

**面向 OPPO / OnePlus / realme Qualcomm SM8750 平台的 6.6 系列内核自动化构建方案**

[![Build](https://img.shields.io/github/actions/workflow/status/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml?branch=main&style=for-the-badge&logo=github-actions&logoColor=white&label=Build)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml)
[![Release](https://img.shields.io/github/v/release/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge&logo=github&label=Latest%20Release)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/releases/latest)
[![Kernel](https://img.shields.io/badge/Kernel-6.6.118-blue?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions)
[![Stars](https://img.shields.io/github/stars/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge&logo=github)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/stargazers)
[![Forks](https://img.shields.io/github/forks/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge&logo=github)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/network/members)
[![License](https://img.shields.io/github/license/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge)](LICENSE)

[🚀 在线编译](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions) · [📦 最新 Release](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/releases/latest) · [💬 Issues](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/issues)

</div>

---

## 📊 自动构建状态

| Workflow | 状态 | 用途 |
|---|---|---|
| 🚀 **SM8750 Kernel Builder** | [![Build](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml/badge.svg?branch=main)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/OPPO_OnePlus_Realme%20SM8750%20Kernel%20Builder.yml) | 主内核自动编译 |
| 🧹 **仓库清理** | [![Clean](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/clean_workflow.yml/badge.svg?branch=main)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/clean_workflow.yml) | 清理工作流 |
| 🗑️ **ccache 清理** | [![Cleaner](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/cleaner.yml/badge.svg?branch=main)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions/workflows/cleaner.yml) | 清理全部 ccache |

> 状态徽章均直接指向仓库当前实际存在的 GitHub Actions Workflow，不使用旧的 workflow 名称或路径。

---

## 📖 项目简介

这是一个针对 **OPPO / OnePlus / realme（欧加真）6.6 系列内核**设计的自动化 Kernel Builder。

项目重点解决官方内核源码、Bazel 构建流程以及厂商定制代码带来的编译门槛，并将 KernelSU、SUSFS、KPM、LZ4/ZSTD、BBR、ADIOS、DroidSpaces、Re-Kernel、基带保护等功能整合到统一的 GitHub Actions 构建流程中。

适用于：

- 自定义 SM8750 / MT6991 内核
- KernelSU / SUSFS 内核构建
- OPPO / OnePlus / realme 内核移植与调试
- GitHub Actions 云端自动编译
- 内核功能组合测试
- 内核版本快速迭代

> **注意：** 第三方内核存在设备、ROM、Boot、DTB、vendor_dlkm、KMI/ABI 等兼容性差异。刷入前请确认平台与内核版本，并准备完整回退方案。

---

## ✨ 核心特性

### 🧩 支持的内核版本

当前主构建 Workflow 提供：

| Kernel | 平台 / 目标 |
|---|---|
| `6.6.30` | SM8750 |
| `6.6.50` | MT6991 / MTK |
| `6.6.56` | SM8750 |
| `6.6.57` | SM8750 |
| `6.6.66` | SM8750 |
| `6.6.89` | SM8750 |
| `6.6.89 MTK` | MTK |
| `6.6.118` | 6.6 新版构建目标 |

**当前 README 标记的主版本：`6.6.118`。** 如果后续 Workflow 的默认目标发生变化，应同步更新顶部 Kernel Badge。

### 🔐 KernelSU

支持选择：

- ReSukiSU
- SukiSU Ultra / ReSukiSU
- KernelSU Next
- 原版 KernelSU
- 无 KernelSU

### 🛡️ SUSFS / KPM

可选集成 SUSFS 与 KPM / KpatchNext，根据 Workflow 参数决定是否编译。

### ⚡ LZ4 / ZSTD / LZ4KD

支持：

- LZ4 1.10.0
- ZSTD 1.5.7
- LZ4KD
- zRAM 相关补丁

### 🌐 网络功能

可选：

- BBR
- TCP 拥塞控制算法
- ipset
- iptables 相关内核配置
- 高级网络功能

### 💾 IO / 容器 / 功耗

支持：

- ADIOS IO Scheduler
- DroidSpaces
- Re-Kernel
- Freezer / NoActive 等配套场景

### 🛡️ 基带保护

可选启用内核级 Baseband Guard，用于降低错误操作或恶意程序对关键非用户分区进行破坏性写入的风险。

> 基带保护不是完整的防砖方案。涉及 `modem`、`efs`、`persist`、`super`、`boot` 等关键分区时仍必须做好备份。

### 🚀 ccache

针对 GitHub Actions 构建环境进行缓存与流程优化，支持：

- ccache 复用
- ccache 更新
- ccache 调试日志
- 自动化产物输出

---

## 🏗️ 构建流程

```text
GitHub Actions
      │
      ├── Kernel Target
      ├── KernelSU
      ├── SUSFS / KPM
      ├── LZ4 / ZSTD / LZ4KD
      ├── BBR / Network
      ├── ADIOS
      ├── DroidSpaces
      ├── Re-Kernel
      ├── Baseband Guard
      └── ccache
             │
             ▼
      Kernel Source / Patches
             │
             ▼
       LLVM / Clang Build
             │
             ▼
        Image / Modules
             │
             ▼
       Release / Artifact
```

---

## 🚀 GitHub Actions

进入：

**Actions → 🚀 OPPO_OnePlus_Realme SM8750 Kernel Builder → Run workflow**

主 Workflow 当前支持以下关键参数：

| 参数 | 默认值 | 作用 |
|---|---|---|
| `kernel_target` | `6.6.89` | 选择内核版本 |
| `ksu_type` | `resukisu` | 选择 KernelSU 分支 |
| `susfs_enable` | `true` | SUSFS |
| `kpm_enable` | `false` | KPM |
| `lz4_enable` | `true` | LZ4/ZSTD |
| `lz4kd_enable` | `false` | LZ4KD |
| `bbr_enable` | `false` | BBR |
| `droidspaces_enable` | `false` | DroidSpaces |
| `better_net` | `false` | 高级网络功能 |
| `adios_enable` | `true` | ADIOS |
| `rekernel_enable` | `false` | Re-Kernel |
| `baseband_guard` | `true` | 基带保护 |
| `ccache_update` | `false` | 更新 ccache |
| `ccache_debug` | `false` | ccache 调试 |

### 推荐 SM8750 日用配置

```text
Kernel       : 6.6.89
KernelSU     : ReSukiSU
SUSFS        : ON
KPM          : OFF
LZ4/ZSTD     : ON
LZ4KD        : OFF
BBR          : OFF
DroidSpaces  : OFF
Better Net   : OFF
ADIOS        : ON
Re-Kernel    : OFF
BasebandGuard: ON
```

---

## 📱 平台支持

### Qualcomm

**SM8750 / Snapdragon 8 Elite**

主要面向采用 SM8750 的 OPPO / OnePlus / realme 设备。

### MediaTek

仓库同时保留 MT6991 / MTK 构建目标。

> **SM8750 与 MT6991 不可交叉刷入。** 必须根据实际 SoC、Boot 链、DTB、vendor_dlkm 与厂商内核 ABI 判断兼容性。

建议刷入前检查：

```bash
getprop ro.soc.model
getprop ro.board.platform
uname -a
getprop ro.build.version.release
```

---

## 📂 项目结构

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

## 📦 Release

GitHub Actions 会生成自动化 Release。

最新 Release：

[![Latest Release](https://img.shields.io/github/v/release/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge&logo=github)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/releases/latest)

Release 中通常包含对应构建配置生成的 **AnyKernel3 ZIP** 等刷入产物。

> Release 的具体内核版本、KernelSU 分支以及功能开关以该 Release 的构建说明为准，不应仅根据 README 顶部 Badge 判断具体刷包配置。

---

## 🔧 本地构建

```bash
git clone https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder.git
cd OPPO_OnePlus_Realme-SM8750-Kernel-Builder
```

具体本地构建入口以当前 `local/` 与 `lib/` 内容为准。推荐普通用户优先使用 GitHub Actions，以避免本地 LLVM、依赖包、ccache 与环境变量不一致造成构建问题。

---

## 🧪 构建产物检查

刷入前建议检查：

```bash
file Image
strings Image | grep -E "Linux version|android"
```

设备端：

```bash
uname -a
getprop ro.boot.slot_suffix
getprop ro.build.version.release
getprop ro.board.platform
```

如果启用了 KernelSU / SUSFS / KPM 等功能，还应确认目标功能实际进入最终 Image，而不是只有构建参数发生变化。

---

## ⚠️ 刷入前注意事项

### 1. 确认 SoC

```text
SM8750 ≠ MT6991
```

不要跨平台刷入。

### 2. 准备回退方案

建议至少备份：

- `boot.img`
- `vendor_boot.img`
- `init_boot.img`（设备存在时）
- `dtbo.img`
- `vbmeta.img`
- 对应版本完整 OTA / 刷机包

### 3. 不要盲目跨 ROM / 跨 KMI

即使 Android 版本相同，也可能存在：

- KMI 不一致
- DTB 不一致
- vendor_dlkm ABI 不一致
- GKI ABI 不一致
- 厂商驱动差异
- Boot Header 差异

因此 **同平台 + 同 Android 版本 ≠ 绝对兼容**。

---

## 🛠️ 开发与贡献

欢迎提交：

- Bug Report
- Kernel Build Failure
- 新设备适配
- 新内核版本适配
- Patch
- CI 优化
- Toolchain 优化
- KernelSU / SUSFS 适配

Issue 建议附带：

```text
设备型号：
SoC：
ROM：
Android：
Kernel：
Boot 版本：
KernelSU：
SUSFS：
Workflow：
完整错误日志：
```

---

## 🙏 Credits

- [ReSukiSU](https://github.com/ReSukiSU/ReSukiSU)
- [SukiSU Ultra](https://github.com/SukiSU-Ultra/SukiSU-Ultra)
- [susfs4ksu](https://github.com/ShirkNeko/susfs4ksu)
- [SukiSU_patch](https://github.com/SukiSU-Ultra/SukiSU_patch)
- [KernelSU Next](https://github.com/pershoot/KernelSU-Next)
- [KernelSU](https://github.com/tiann/KernelSU)
- [WildKernels/kernel_patches](https://github.com/WildKernels/kernel_patches)
- [ADIOS](https://github.com/firelzrd/adios)
- [Mountify](https://github.com/backslashxx/mountify)
- [Baseband Guard](https://github.com/vc-teahouse/Baseband-guard)

感谢所有提供源码、补丁、设备树、测试反馈与构建经验的开发者和用户。

---

## 📜 License

本仓库中的构建脚本、补丁及其他内容以各目录或文件中声明的许可证为准。

第三方内核源码、补丁、工具链及项目不自动继承本仓库的许可证，请遵守对应上游项目的许可证与源码发布要求。

---

<div align="center">

**Built for Kernel Developers · OPPO / OnePlus / realme · SM8750 / 6.6**

⭐ 如果这个项目对你有帮助，欢迎 Star。

</div>
