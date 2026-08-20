# 插件护士 - QQ ChainScope 1.4.3

**Qing Audio 官方下载与发布页 / Official downloads and releases by Qing Audio**

> QQ ChainScope 不是单纯的 A/B 按钮或频谱仪。它直接工作在真实 DAW 工程中，用于比较整条处理链、进行公平响度匹配、校准相位/极性与左右电平、修正残余延迟，并集中比较多个处理方案。
>
> QQ ChainScope is more than an A/B button or spectrum analyzer. It works inside real DAW sessions to compare complete processing chains, loudness-match fairly, calibrate phase/polarity and L/R balance, rescue residual timing errors, and compare multiple processing choices.

**QQ ChainScope 是专有闭源软件。** 本公共仓库只提供允许公开分发的插件成品、文档、截图与版本说明，不包含源代码。

**QQ ChainScope is proprietary closed-source software.** This public repository contains approved binaries, documentation, screenshots, and release information only; source code is not included.

<p align="center">
  <img src="assets/screenshots/02-mixboard-expanded-v1.2.17.png" alt="QQ ChainScope Mixboard" width="100%">
</p>

## 最新版本 / Latest release

**QQ ChainScope 1.4.3（2026-08-20）** 是当前稳定版。

**QQ ChainScope 1.4.3 (2026-08-20)** is the current stable release.

- **[下载 v1.4.3 / Download v1.4.3](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/releases/tag/v1.4.3)**
- **[v1.2.17 → v1.4.3 完整双语更新记录 / Full bilingual changelog](./RELEASE_NOTES_1.4.3.md)**
- **[全部版本 / All releases](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/releases)**
- **[Issues / Bugs & Feedback](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/issues)**

本次提供经过本机编译、Steinberg VST3 Validator 验证并与系统安装副本核对一致的 **Windows x64 VST3**。本次暂未提供 macOS 1.4.3 生成物；旧版本 macOS 文件不会被改名冒充 1.4.3。

This release provides locally built and validated **Windows x64 VST3** binaries. macOS 1.4.3 artifacts are not currently included; older macOS binaries are never relabeled as 1.4.3.

## 三个组件，一套工作流 / Three components, one workflow

| 插件 / Plug-in | 作用 / Role |
|---|---|
| `QQ-A-Send-ChainScope.vst3` | 放在处理链前，捕获 Original，并创建或选择 Group。 / Place before the chain to capture Original and create/select a Group. |
| `QQ-B-Return-ChainScope.vst3` | 放在处理链后，负责测量、Dry/Wet、Bypass、校准、EQ Match、图表与 Chain Note。 / Place after the chain for measurement, Dry/Wet, bypass, calibration, EQ Match, graphs, and Chain Note. |
| `QQ-C-Mixboard-ChainScope.vst3` | 比较 Original 与最多四个 Return，并提供集中监听。 / Compare Original with up to four Returns and provide centralized monitoring. |

Single Return：

```text
QQ-A-Send-ChainScope -> plug-in / hardware chain -> QQ-B-Return-ChainScope (FINAL)
```

Multi Return：

```text
Send -> Process A -> Return 1 -> Process B -> Return 2 -> ... -> Return 4 (FINAL) -> Mixboard
```

Multi Return 中，每个非 FINAL Return 记录自己的处理结果，再把时间对齐的 Original 交给下一套处理，因此 R1–R4 是从同一 Original 出发的独立方案，不是累积 A+B+C+D。

In Multi Return, each non-FINAL Return captures its own result and passes the aligned Original onward. R1–R4 are independent choices based on the same source, not cumulative A+B+C+D processing.

## 主要能力 / Highlights

- Before / After / Difference：Integrated LUFS、Peak、True Peak、播放段平均 RMS。
- Spectrum、Waveform、WaveScope 与停止播放后的最后一帧保持。
- 处理链级 Dry/Wet、时间对齐 QQ Bypass、PHASE、Polarity、L/R Cal 与 Latency Rescue。
- 高精度停止后校准：播放时采集，Stop 后统一结算。
- 线性相位 EQ Match：Amount、Smooth、10/20/40/80、完整传递曲线与高精度低频/频带功率分析。
- Mixboard Monitor：ST、MONO、L、R、SIDES、SIP，以及 LOW / Band Pass / HIGH 频段试听。
- Chain Note：把文字、图片、硬件设置和接线说明随工程保存。

- Before / After / Difference with Integrated LUFS, Peak, True Peak, and transport-segment RMS.
- Spectrum, Waveform, WaveScope, and last-frame hold after transport stop.
- Chain-level Dry/Wet, aligned bypass, PHASE, polarity, L/R calibration, and Latency Rescue.
- High-precision stopped calibration: capture during playback and finalize after Stop.
- Linear-phase EQ Match with Amount, Smooth, 10/20/40/80, full-transfer curves, and high-precision LF/band-power analysis.
- Mixboard Monitor with ST, MONO, L, R, SIDES, SIP, and LOW / Band Pass / HIGH audition.
- Chain Note for text, images, hardware settings, and cabling notes saved with the project.

## 从 v1.2.17 到 v1.4.3 / From v1.2.17 to v1.4.3

本次公开更新跨越 1.2.18、1.3.0–1.3.10、1.4.0–1.4.3。窗口恢复、EQ Match、停止后校准、Standalone、文件命名、低频/频带分析、IR 交叉淡化与 Mixboard Monitor 都有显著变化。

完整记录不是一段笼统摘要，而是按每个中间版本分别列出新增、修复和行为变化：**[查看完整 Release Notes](./RELEASE_NOTES_1.4.3.md)**。

This public update spans 1.2.18, 1.3.0–1.3.10, and 1.4.0–1.4.3. Window restoration, EQ Match, stopped calibration, Standalone behavior, bundle naming, LF/band analysis, IR crossfades, and Mixboard Monitor all changed substantially. See the **[full version-by-version Release Notes](./RELEASE_NOTES_1.4.3.md)**.

## v1.4.3 附件 / v1.4.3 assets

- `QQ-ChainScope-1.4.3-Windows-x64-VST3.zip`
- `QQ-ChainScope-1.4.3-Installation-Guide-Chinese.txt`
- `QQ-ChainScope-1.4.3-Installation-Guide-English.txt`
- `QQ-ChainScope-1.4.3-Release-Notes-Bilingual.md`
- `QQ-ChainScope-1.4.3-SHA256SUMS.txt`

三个插件必须保持相同版本并一起更新。

All three plug-ins must remain on the same version and be updated together.

## Windows 安装 / Windows installation

1. 完全关闭 DAW。
2. 从 `C:\Program Files\Common Files\VST3` 删除所有三个旧版 QQ ChainScope bundle，包括旧空格命名。
3. 解压 Windows 包，把三个新的连字符命名 `.vst3` 文件夹完整复制到该目录。
4. 重新打开 DAW，必要时执行完整重扫。

Close the DAW, remove all three older QQ ChainScope bundles (including older space-separated names), copy the three complete hyphenated `.vst3` folders to `C:\Program Files\Common Files\VST3`, then reopen/rescan the DAW.

请在安装前阅读 Release 中的中英文安装说明。直接保留旧版再复制新版，可能让 DAW 扫描到重复插件或误插旧版。

Read the included installation guide before upgrading. Keeping older bundles beside the new ones can create duplicate entries or load the wrong version.

## 兼容性与已知限制 / Compatibility and known limitations

| 项目 / Item | v1.4.3 |
|---|---|
| 平台 / Platform | Windows x64 |
| 格式 / Format | VST3 |
| 宿主 / Host | 64-bit VST3-compatible DAW |

- 如果 DAW 仍缓存旧条目，请清除旧 bundle、插件缓存并完整重扫。
- 旧工程升级后请检查 Send / Return / Mixboard 实例、Group、FINAL 与路由。
- 1.2.17 的旧 PDF 手册没有作为 1.4.3 手册重新发布，因为界面和功能说明已过时；当前以 1.4.3 Release Notes 与安装说明为准。
- macOS 1.4.3 VST3/AU 当前未包含在本次 Release 中。

- If the DAW retains cached entries, remove older bundles, clear the plug-in cache as appropriate, and perform a full rescan.
- After upgrading older projects, verify Send / Return / Mixboard instances, Group, FINAL, and routing.
- The older 1.2.17 PDF manuals are not republished as 1.4.3 manuals because their UI/feature descriptions are outdated. Use the 1.4.3 Release Notes and installation guides.
- macOS 1.4.3 VST3/AU artifacts are not included in this Release.

## 问题与反馈 / Bugs & feedback

请使用本仓库的 [Issues](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/issues)，并附上操作系统、DAW/版本、ChainScope 版本、Single/Multi Return 拓扑、实际 Insert 顺序、复现步骤和截图/录屏（如有）。

Use [Issues](https://github.com/Ziqing-Gu/Plugin-Nurse-QQ-ChainScope-Release/issues) and include OS, DAW/version, ChainScope version, Single/Multi Return topology, actual insert order, reproduction steps, and screenshots/video when available.

## 许可 / License

Copyright © Ziqing Gu. All rights reserved. QQ ChainScope is proprietary software. Modification or redistribution of its binaries is not authorized unless separately permitted by the author.
