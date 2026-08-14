# 插件护士 - QQ ChainScope

**Qing Audio 官方下载与发布页 / Official downloads and releases by Qing Audio**

QQ ChainScope 是一套运行在真实 DAW 工程中的处理链检查、匹配、校准、记录与横向比较工具。它不只是 A/B 按钮，也不只是频谱分析仪；你可以把它理解为陪伴插件与外部硬件工作的“插件护士”。

QQ ChainScope is a practical DAW toolset for checking, matching, calibrating, documenting, and comparing plug-in or external-hardware processing chains. It is more than an A/B button or spectrum analyzer - think of it as a “plug-in nurse” working alongside your processing chain.

> **QQ ChainScope 是专有软件，不开源。本公开仓库只提供编译后的插件成品、文档和版本说明；源码仓库保持私有。**  
> **QQ ChainScope is proprietary software and is not open source. This public repository contains compiled plug-ins, documentation, and release information only; the source repository remains private.**

## 最新版本 / Latest Release

**QQ ChainScope 1.2.14** 是当前最新、最稳定版本。  
**QQ ChainScope 1.2.14** is the current latest and most stable release.

- [下载 v1.2.14 / Download v1.2.14](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/releases/tag/v1.2.14)
- [全部版本 / All releases](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/releases)

## 三个组件，一套工作流 / Three Components, One Workflow

| 组件 / Component | 用途 / Purpose |
|---|---|
| **QQ ChainScope A Send** | 放在处理链之前，捕获未处理的 Original，并创建或选择 Group。 / Place before the chain to capture the unprocessed Original and create or select a Group. |
| **QQ ChainScope B Return** | 放在处理链之后，负责测量、Dry/Wet、QQ Bypass、PHASE、Latency Rescue、图表和 Chain Note。 / Place after the chain for measurement, Dry/Wet, QQ Bypass, PHASE, Latency Rescue, graphs, and Chain Note. |
| **QQ ChainScope C Mixboard** | 比较 Original 与最多四个 Return 结果；使用时必须放在 FINAL Return 之后。 / Compare Original with up to four Return results; when used, it must be placed after the FINAL Return. |

推荐结构 / Recommended topology:

~~~text
A Send -> processing chain -> B Return (FINAL) -> C Mixboard (optional)
~~~

同一 Group 应放在同一 Track 的串行 Insert 链上。每个 Group 支持一个 Send、一个到四个 Return，以及一个可选的 Mixboard。  
Keep one Group on one serial Insert chain in the same Track. A Group supports one Send, one to four Returns, and an optional Mixboard.

## 主要功能 / Features

- 处理前后比较：Peak、True Peak、播放段平均 RMS、Integrated LUFS、Spectrum、Waveform 和 WaveScope。  
  Before/after comparison: Peak, True Peak, playback-average RMS, Integrated LUFS, Spectrum, Waveform, and WaveScope.
- 使用 Match 进行响度匹配，减少“更响就是更好”的误判。  
  Loudness matching with Match for fairer comparisons.
- 为单个插件、完整插件链或外部硬件链增加时间对齐的 Dry/Wet。  
  Time-aligned Dry/Wet for a plug-in, complete plug-in chain, or external-hardware chain.
- PHASE 相位对齐，以及用于残余时序误差的 Latency Rescue。  
  PHASE alignment and Latency Rescue for residual timing errors.
- Cal 校准处理链额外引入的左右声道平均 RMS 差异。  
  Cal corrects additional L/R playback-average RMS imbalance introduced by the chain.
- Chain Note 将文字、路由说明和硬件设置图片随 DAW 工程保存。  
  Chain Note stores text, routing notes, and hardware-setting images with the DAW project.
- Mixboard 从同一 Original 出发比较最多四套独立处理方案。  
  Mixboard compares up to four independent processing choices that begin from the same Original.
- FULL / ECO 显示分析模式；离线导出时自动停止显示分析，音频 DSP 继续工作。  
  FULL / ECO display-analysis modes; offline render disables display analysis while audio DSP remains active.

## 系统要求 / Requirements

| 平台 / Platform | 格式与架构 / Format and Architecture |
|---|---|
| Windows | 64-bit VST3 / x64 |
| macOS Apple Silicon | VST3 / native arm64 |
| macOS Intel | VST3 / native x86_64 |
| macOS AU | Universal 2 / arm64 + x86_64 |
| macOS 最低目标系统 / Deployment target | macOS 11 or later |

A Send、B Return 和 C Mixboard 必须保持同一版本，并一起更新。  
A Send, B Return, and C Mixboard must remain on the same version and be updated together.

## 下载 / Downloads

v1.2.14 Release 提供以下独立下载：  
The v1.2.14 Release provides these separate downloads:

- **QQ-ChainScope-1.2.14-Windows-x64-VST3.zip**
- **QQ-ChainScope-1.2.14-macOS-Apple-Silicon-VST3.zip**
- **QQ-ChainScope-1.2.14-macOS-Intel-VST3.zip**
- **QQ-ChainScope-1.2.14-macOS-Universal-2-AU.zip**
- 中英文安装说明与 PDF 用户手册 / Chinese and English installation guides and PDF user manuals
- **QQ-ChainScope-1.2.14-SHA256SUMS.txt**

## 安装 / Install

### Windows VST3

完全退出 DAW，解压 Windows 包，并将三个 .vst3 文件夹复制到：

~~~text
C:\Program Files\Common Files\VST3
~~~

Quit the DAW, extract the Windows package, and copy all three .vst3 folders to the path above. Replace all three older plug-ins together, then rescan VST3 plug-ins.

### macOS VST3

Apple Silicon 原生宿主选择 Apple Silicon 包；Intel Mac 或 Rosetta 模式的 Intel 宿主选择 Intel 包。**不要同时安装两套 VST3 架构包。**

Choose the Apple Silicon package for native Apple Silicon hosts, or the Intel package for Intel Macs and Intel hosts under Rosetta. **Do not install both VST3 architecture packages.**

用户目录 / Per-user folder:

~~~text
~/Library/Audio/Plug-Ins/VST3
~~~

### macOS Audio Unit

解压 Universal 2 AU 包，并将三个 .component 文件夹复制到：

~~~text
~/Library/Audio/Plug-Ins/Components
~~~

Extract the Universal 2 AU package and copy all three .component folders to the path above.

macOS 插件经过临时签名与构建验证，但未使用 Apple Developer ID 公证。若系统阻止加载，请只在确认文件来自本仓库 Release 后，按照随包安装说明处理 quarantine 属性。  
The macOS plug-ins are ad-hoc signed and build-validated, but are not notarized with an Apple Developer ID. If macOS blocks them, follow the included installation guide only after confirming the files came from this repository's Release.

完整步骤请阅读 Release 中的中英文安装说明。  
For complete steps, read the Chinese or English installation guide included in the Release.

## 使用手册 / User Manuals

v1.2.14 Release 包含 28 页中文用户手册和 28 页英文用户手册，涵盖快速开始、单 Return / Multi Return、FINAL 规则、Mixboard、测量、PHASE、Latency Rescue、Spectrum、Waveform / WaveScope、Chain Note、FULL / ECO、故障排查和快捷操作。

The v1.2.14 Release includes 28-page Chinese and English manuals covering quick start, Single Return / Multi Return, FINAL rules, Mixboard, measurement, PHASE, Latency Rescue, Spectrum, Waveform / WaveScope, Chain Note, FULL / ECO, troubleshooting, and shortcuts.

## 许可与使用 / License & Usage

QQ ChainScope 为 Qing Audio 的专有软件，不开源。公开下载内容仅包含编译后的插件成品与文档，不包含源码。其他许可与使用条款以 Qing Audio 后续发布内容为准。  
QQ ChainScope is proprietary Qing Audio software and is not open source. Public downloads contain compiled plug-ins and documentation only, with no source code. Additional license and usage terms will be published by Qing Audio when applicable.

## 问题与反馈 / Bugs & Feedback

请通过本仓库的 [Issues](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/issues) 提交可复现的问题，并附上操作系统、DAW、插件格式、架构和复现步骤。  
Please use this repository's [Issues](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/issues) for reproducible reports, including your OS, DAW, plug-in format, architecture, and reproduction steps.

## 截图 / Screenshots

中英文用户手册包含带标注的界面截图；后续可在本节增加独立产品图。  
The Chinese and English user manuals include annotated interface screenshots; standalone product images may be added here later.