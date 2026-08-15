# OPPO / OnePlus / realme SM8750 Kernel Builder

<div align="center">

**面向 OPPO / OnePlus / realme Qualcomm SM8750 平台的 6.6 系列内核自动化构建方案**

[![GitHub Workflow](https://img.shields.io/github/actions/workflow/status/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/OPPO_OnePlus_RealMe%20SM8750%20Kernel%20Builder.yml?style=for-the-badge&logo=github-actions&logoColor=white&label=Build)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions)
[![Stars](https://img.shields.io/github/stars/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge&logo=github)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/stargazers)
[![Forks](https://img.shields.io/github/forks/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder?style=for-the-badge&logo=github)](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/network/members)
[![License](https://img.shields.io/github/license/HeiKe-Tom/OPPO_OnePlus_RealMe-SM8750-Kernel-Builder?style=for-the-badge)](LICENSE)

[🚀 在线编译](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/actions) · [💬 Issues](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/issues) · [📦 Releases](https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder/releases)

</div>

---

## 📖 项目简介

这是一个针对 **OPPO / OnePlus / realme（欧加真）6.6 系列内核**设计的自动化 Kernel Builder。

项目重点解决官方内核源码、Bazel 构建流程以及厂商定制代码带来的编译门槛，并将 KernelSU、SUSFS、KPM、LZ4/ZSTD、BBR、ADIOS、DroidSpaces、Re-Kernel、基带保护等功能整合到统一的 GitHub Actions 构建流程中。

目前工作流提供多种内核版本和可选功能，适合用于：

- 自定义 SM8750 / MT6991 内核
- KernelSU / SUSFS 内核构建
- OPPO / OnePlus / realme 内核移植与调试
- GitHub Actions 云端自动编译
- 内核功能模块化组合测试
- 日常内核版本快速迭代

> **注意：** 本项目生成的内核属于第三方自定义内核。不同设备、ROM、Boot 版本以及厂商内核分支之间存在兼容性差异。刷入前请确认设备平台、内核版本、Boot 镜像结构以及回退方案。

---

## ✨ 核心特性

### 🧩 多内核版本

当前 GitHub Actions 工作流支持选择：

| Kernel | 平台 / 来源定位 |
|---|---|
| `6.6.30` | SM8750 系列 |
| `6.6.50` | MT6991 / 天玑平台 |
| `6.6.56` | SM8750 系列 |
| `6.6.57` | SM8750 系列 |
| `6.6.66` | SM8750 系列 |
| `6.6.89` | SM8750 系列，当前主要版本之一 |
| `6.6.89 MTK` | MTK 分支目标 |
| `6.6.118` | 新版 6.6 内核构建目标 |

> 实际可刷入性取决于设备 DTB/DTBO、vendor_dlkm、模块 ABI、厂商驱动以及 Boot 链路，不应仅依据内核版本号判断兼容性。

### 🔐 KernelSU 多分支支持

工作流可选择：

- **ReSukiSU**
- **SukiSU Ultra**（当前上游仓库已重定向至 ReSukiSU）
- **KernelSU Next**
- **原版 KernelSU**
- **无 KernelSU**

### 🛡️ SUSFS

可选集成 SUSFS，用于增强 KernelSU 环境下的隐藏、挂载以及相关内核能力。

### ⚡ KPM / KpatchNext

可选集成 KPM，并使用独立的 KpatchNext 实现，使 KPM 不强依赖特定 KernelSU / Magisk 环境。

### 🚀 LZ4 / ZSTD

提供：

- LZ4 1.10.0
- ZSTD 1.5.7
- 对应内核补丁
- 可选 LZ4KD 支持

用于改善压缩相关能力，并为 zRAM 等场景提供更现代的算法支持。

### 🌐 网络功能

可选：

- BBR
- 高级网络功能
- ipset
- iptables 相关内核配置
- 其他 TCP 拥塞控制算法

BBR 默认并不强制开启为系统默认算法，是否启用应根据实际网络场景决定。

### 💾 IO 调度

集成 **ADIOS IO Scheduler**，可在工作流中直接选择是否启用。

### 📦 DroidSpaces

提供 DroidSpaces 容器支持，并区分：

- `false`：关闭
- `standard`：基础容器 + `ntsync`
- `extend`：额外测试支持

### 🧊 Re-Kernel

可选启用 Re-Kernel，用于与 Freezer、NoActive 等工具配合实现更深层的应用冻结与功耗管理。

### 🛡️ 内核级基带保护

工作流默认开启基带保护选项，用于降低恶意脚本或错误操作对关键非用户分区进行破坏性写入的风险。

> 基带保护属于防护机制，不等同于完整的设备防砖方案。任何涉及 `modem`、`efs`、`persist`、`super`、`boot` 等关键分区的操作仍应提前做好完整备份。

### 🚀 ccache / 编译优化

项目使用缓存机制减少重复编译时间，并针对 GitHub Actions 环境进行构建流程优化。

工作流同时支持：

- ccache 更新
- ccache 调试日志
- 自动缓存复用
- 多版本构建参数
- 自动化产物输出

---

## 🏗️ 构建架构

```text
GitHub Actions
      │
      ├── 选择 Kernel 版本
      ├── 选择 KernelSU 分支
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
       GitHub Actions Artifact
```

---

## 🚀 GitHub Actions 使用方法

打开：

**Actions → OPPO_OnePlus_Realme SM8750 Kernel Builder → Run workflow**

然后根据需求选择参数。

### 基础参数

| 参数 | 说明 | 默认值 |
|---|---|---|
| `kernel_target` | 内核版本 | `6.6.89` |
| `ksu_type` | KernelSU 分支 | `resukisu` |
| `susfs_enable` | SUSFS | `true` |
| `kpm_enable` | KPM | `false` |
| `lz4_enable` | LZ4/ZSTD 补丁 | `true` |
| `lz4kd_enable` | LZ4KD | `false` |
| `bbr_enable` | BBR 模式 | `false` |
| `droidspaces_enable` | DroidSpaces | `false` |
| `better_net` | 高级网络功能 | `false` |
| `adios_enable` | ADIOS | `true` |
| `rekernel_enable` | Re-Kernel | `false` |
| `baseband_guard` | 基带保护 | `true` |
| `ccache_update` | 更新 ccache | `false` |
| `ccache_debug` | 上传 ccache 调试日志 | `false` |
| `kernel_suffix` | 自定义内核版本后缀 | 默认 Android 15 内核标识 |

### 推荐的 SM8750 日用配置

如果目标是 **OnePlus / OPPO / realme SM8750 + Android 15/16 系列 ROM**，可以优先使用：

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

如果需要测试新内核代码，则可以进一步尝试 `6.6.118`，但应先确认对应设备的源码、DTB、模块 ABI 和启动链兼容性。

---

## 📱 平台支持

### Qualcomm

**SM8750 / Snapdragon 8 Elite**

主要面向 OPPO / OnePlus / realme 采用 SM8750 的设备。

### MediaTek

项目同时保留 MT6991 / 相关 MTK 构建目标，但 **MTK 内核不能与 SM8750 内核混用**。

刷入前必须确认：

```text
ro.soc.model
ro.board.platform
uname -a
getprop ro.build.version.release
```

以及实际 Boot / vendor_boot / dtbo / vendor_dlkm 结构。

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
├── droidspaces_patch/       # DroidSpaces 相关补丁
├── lib/                     # 构建脚本与公共函数
├── local/                   # 本地构建相关内容
├── other_patch/             # 其他内核补丁
├── zram_patch/              # zRAM / 压缩算法相关补丁
├── zram.zip                 # zRAM 相关构建资源
└── README.md
```

---

## 🔧 本地构建

项目核心逻辑同时面向本地 Shell 环境设计，但具体本地构建入口会随着工作流版本迭代调整。

推荐优先使用 GitHub Actions：

```bash
git clone https://github.com/HeiKe-Tom/OPPO_OnePlus_Realme-SM8750-Kernel-Builder.git
cd OPPO_OnePlus_Realme-SM8750-Kernel-Builder
```

然后根据仓库当前 `local/` 与 `lib/` 中的脚本执行对应构建流程。

> 不建议直接复制旧版本命令进行本地构建。内核版本、工具链、补丁以及环境依赖可能发生变化。

---

## 🧪 构建产物检查

刷入之前建议至少检查：

```bash
file Image
strings Image | grep -E "Linux version|android"
```

设备端可以检查：

```bash
uname -a
getprop ro.boot.slot_suffix
getprop ro.build.version.release
getprop ro.board.platform
```

如果使用 KernelSU / SUSFS / KPM 等附加功能，还应确认对应功能是否实际编译进目标内核，而不是仅仅存在于构建参数中。

---

## ⚠️ 刷入前注意事项

### 1. 必须确认平台

```text
SM8750 ≠ MT6991
```

不要因为两个平台都属于高端 Android SoC，就尝试交叉刷入。

### 2. 必须准备回退方案

建议至少保留：

- 原厂 `boot.img`
- 原厂 `vendor_boot.img`
- 原厂 `dtbo.img`
- 对应版本完整 OTA / 刷机包
- 当前版本的 KernelSU / Magisk 恢复方案

### 3. 不要盲目跨版本刷入

即使两个 ROM 都是 Android 15 / Android 16，也可能存在：

- KMI 不一致
- DTB 不一致
- vendor_dlkm ABI 不一致
- GKI ABI 不一致
- 厂商驱动差异
- boot header 差异

因此 **“同平台 + 同 Android 版本”不代表绝对兼容**。

### 4. 基带保护不是万能防砖

Baseband Guard 可以降低部分恶意或误操作导致的关键分区写入风险，但不能替代完整备份。

涉及 EDL、fastboot、super、modem、NV、EFS 等操作时仍需谨慎。

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

提交 Issue 时请尽可能附带：

```text
设备型号：
SoC：
ROM：
Android：
Kernel：
Boot 版本：
KernelSU：
SUSFS：
失败的 Workflow：
完整错误日志：
```

这样可以显著提高问题定位效率。

---

## 🙏 Credits

本项目使用或参考了大量优秀的开源项目与社区工作：

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

同时感谢所有提供内核源码、设备树、补丁、测试反馈以及构建经验的开发者与用户。

---

## 📜 License

本仓库中的构建脚本、补丁及其他内容请以各目录或文件中声明的许可证为准。

**第三方内核源码、补丁及工具链不自动继承本仓库的许可证。** 使用前请遵守对应上游项目的许可证及源码发布要求。

---

<div align="center">

### Built for Kernel Developers · OPPO / OnePlus / realme · SM8750 / 6.6

**如果这个项目对你有帮助，欢迎 ⭐ Star。**

</div>
