# QQ ChainScope 1.4.3 Release Notes / 更新说明

**Release date / 发布日期:** 2026-08-20  
**Previous public release / 上一个公开版本:** 1.2.17  
**Current release / 当前版本:** 1.4.3

本次公开发布跨越 1.2.18、1.3.0–1.3.10、1.4.0–1.4.3。下面按版本逐项说明相对上一版本的新增、修复及行为变化，而不是只描述 1.4.3 的最后一次改动。

This public release spans 1.2.18, 1.3.0–1.3.10, and 1.4.0–1.4.3. The sections below document each intermediate version relative to the version immediately before it.

## 1.2.18 — Window Restore Fix / 窗口恢复修复

- 修复 Cubase 恢复工程时使用陈旧 wrapper/editorScale 信息，导致 Return 首次打开窗口异常巨大的问题。
- 加入启动尺寸保护；DSP、路由和音频结果不变。
- Fixed an oversized Return editor on the first open after Cubase project restore, caused by stale wrapper/editorScale state.
- Added a startup-size guard without changing DSP, routing, or audio output.

## 1.3.0 — Spectrum Slope & Linear-Phase EQ Match

- 新增频谱显示斜率 0–6 dB/oct，以 1 kHz 为支点；只改变显示，不改变声音。
- 新增线性相位 EQ Match，提供 CAL、RESET、MATCH，以及 10/20/40/80 四档分析/匹配设置。
- 新增 PHASE 20 设置，并将相关默认值相互独立。
- 完成高频匹配细化和频谱斜率旋钮交互。
- Added a display-only 0–6 dB/oct spectrum slope pivoted at 1 kHz.
- Added linear-phase EQ Match with CAL, RESET, MATCH, and 10/20/40/80 settings.
- Added PHASE 20, independent defaults, high-frequency refinement, and the finished slope-knob interaction.

## 1.3.1 — Independent Calibration & Unified Stopped CAL

- 将 PHASE CAL 与 EQ CAL 解耦，Dry/Wet 调整不再清除 Match。
- Bypass 的处理顺序移动到 Monitor 之前，避免监听状态影响旁路预期。
- 校准改为播放时采集、停止后统一计算；同一遍播放可重复、与操作顺序无关。
- 保存停止时的 EQ AVG 快照，避免 PDC 重新准备后丢失采集结果。
- Decoupled PHASE CAL from EQ CAL; Dry/Wet no longer clears Match.
- Moved bypass handling before monitor processing.
- Calibration now captures during playback and finalizes after transport stop, producing repeatable, order-independent results from the same pass.
- Preserved the committed stopped EQ AVG snapshot across PDC re-preparation.

## 1.3.2 — Standalone Delta & Naming Cleanup

- Standalone 模式新增 None/无来源状态。
- 调整 Delta 区域布局与显示。
- 三个实际 VST3 文件名改为统一连字符命名：`QQ-A-Send-ChainScope.vst3`、`QQ-B-Return-ChainScope.vst3`、`QQ-C-Mixboard-ChainScope.vst3`。
- Added an explicit None source in Standalone mode, refined the Delta layout, and standardized all three bundle names with hyphens.

## 1.3.3 — High-Precision Detached Calibration

- 提升 Match 的计算精度。
- 修复 Bypass 启动阶段短暂出现 Wet 信号的问题。
- 校准后的 Return 脱离 Send 后可进入 Standalone，同时保留已提交的测量与匹配模型。
- Improved Match precision, fixed a brief Wet burst during bypass startup, and allowed a calibrated Return to detach into Standalone while retaining committed models.

## 1.3.4 — LF Match & Phase/Polarity

- 低频匹配改用 16384 点 Goertzel/Hann 高精度分析。
- 恢复并明确 PHASE/Polarity 的意图和显示行为。
- Improved low-frequency matching with a 16384-point Goertzel/Hann analysis and restored the intended PHASE/polarity behavior.

## 1.3.5 — Unified High-Precision AVG & Polarity Metadata

- AVG 与 Mixboard 统一使用高精度分析结果，减少不同视图之间的偏差。
- PHASE 极性元数据升级为 QCP9，增强跨插件传递的一致性。
- Unified high-precision AVG/Mixboard analysis and introduced QCP9 phase/polarity metadata for consistent cross-plug-in transfer.

## 1.3.6 — EQ Match Amount & Curve

- 新增 EQ Match Amount，可连续控制匹配强度。
- 新增匹配曲线显示，使计算结果和实际施加量更直观。
- Added continuous EQ Match Amount control and a visible match curve.

## 1.3.7 — Band-Power EQ Match

- EQ Match 改用 16384 点 FFT 频带功率分析。
- 移除原有 -100 dB 地板，改善极低电平与频带差异的处理。
- Switched EQ Match to 16384-point FFT band-power analysis and removed the fixed -100 dB floor.

## 1.3.8 — Full Transfer & Smooth

- 匹配曲线扩展为完整传递函数，而非只处理局部差异。
- 新增 Smooth 控制。
- 匹配数据格式升级为 QEM2。
- 固定 AVG/PEAK 槽位语义，避免视图/状态切换时含义漂移。
- Expanded EQ Match to a full-transfer curve, added Smooth, introduced QEM2 data, and fixed AVG/PEAK slot semantics.

## 1.3.9 — UI Defaults & IR Crossfade

- 调整界面默认值与初始状态。
- 线性相位处理采用双卷积器 IR 预热/交叉淡化。
- 修复快速拖动参数时可能出现的卡顿与声音中断。
- Refined UI defaults and startup state, added dual-convolver IR warm-up/crossfade, and fixed stutter during rapid parameter dragging.

## 1.3.10 — Final UI Polish

- 仅将控制行整体下移 8 px，完成最终界面对齐。
- 音频处理、参数含义和工程兼容性不变。
- Moved the control row down by 8 px for final alignment; DSP and parameter behavior were unchanged.

## 1.4.0 — Mixboard Monitor

- Mixboard 新增完整监听系统：ST、MONO、L、R、SIDES 与 SIP。
- 新增 Monitor Filter、斜率和频段选择。
- 监听与滤波切换使用约 80 ms 交叉淡化，减少爆音。
- 统一听觉结果与界面状态。
- Added the Mixboard Monitor system with ST, MONO, L, R, SIDES, SIP, Monitor Filter, slopes, and band selection.
- Added an approximately 80 ms crossfade and aligned audible behavior with visual state.

## 1.4.1 — Mixboard Monitor UX

- 改进监听来源选择与眼睛图标状态。
- SIP 默认行为调整。
- L/R 单声道试听加入仅作用于监听的 -3.0103 dB 增益补偿。
- 压缩 Monitor Filter 区域，使操作更集中。
- Improved source selection and eye-state feedback, refined SIP defaults, added monitor-only -3.0103 dB gain compensation for L/R audition, and compacted the filter UI.

## 1.4.2 — Monitor Filter Audition

- 修正试听语义：LOW CUT 试听 LOW 以下，Band Pass 试听 LOW–HIGH，HIGH CUT 试听 HIGH 以上。
- 调整 Filter slope 控件行。
- SIP OFF 的 SIDES 试听加入 -3.0103 dB 补偿。
- Corrected audition semantics: LOW CUT hears below LOW, Band Pass hears LOW–HIGH, and HIGH CUT hears above HIGH.
- Refined the slope row and added -3.0103 dB compensation for SIDES when SIP is off.

## 1.4.3 — Band Select Forces Band Pass

- 在 Mixboard 中点击频段选择时，监听模式现在会明确切换为 Band Pass。
- 修复用户选择频段后仍残留 Low Cut/High Cut 模式、造成实际试听内容与操作意图不一致的问题。
- Selecting an audition band in Mixboard now explicitly forces Band Pass mode.
- Fixed the mismatch where a previous Low Cut/High Cut mode could remain active after band selection.

## Compatibility and behavior notes / 兼容性与行为说明

- 1.4.3 公共生成物为 Windows x64 VST3，需要 64 位 VST3 宿主。
- 1.3.2 起实际文件名使用连字符命名，升级时必须先删除旧版三个插件，避免 DAW 同时扫描到重复项。
- 旧工程如果引用旧文件名，建议保留工程备份，并在升级后确认 Send、Return、Mixboard 的实例与路由。
- EQ Match、校准和 Mixboard Monitor 在 1.3.x/1.4.x 中有明显行为扩展；请不要把 1.2.17 的旧手册当作完整的 1.4.3 操作说明。
- The public 1.4.3 artifact is Windows x64 VST3 and requires a 64-bit VST3 host.
- Bundle names use hyphens from 1.3.2 onward. Remove all three older bundles before copying the new version to prevent duplicate DAW entries.
- Back up projects that reference older bundle names, then confirm Send/Return/Mixboard instances and routing after upgrading.
- Calibration, EQ Match, and Mixboard Monitor changed substantially; the old 1.2.17 manuals are not a complete guide to 1.4.3.

## Installation / 安装

关闭 DAW，删除所有旧命名的三个 QQ ChainScope VST3，再把压缩包中的三个新插件复制到 `C:\Program Files\Common Files\VST3`，重新打开 DAW 并在必要时完整重扫。详细步骤见中英文安装说明。

Close the DAW, remove all three older QQ ChainScope bundles, copy the three new bundles to `C:\Program Files\Common Files\VST3`, then reopen the DAW and perform a full rescan if needed. See the included installation guides.

## Known limitations / 已知限制

- 当前 Release 未包含 macOS 1.4.3 VST3/AU；旧版 macOS 文件未改名复用。
- 当前没有与 1.4.3 界面和功能完全同步的 PDF 手册，Release Notes 与安装说明是当前文档依据。
- This Release does not include macOS 1.4.3 VST3/AU artifacts; older macOS binaries are not relabeled.
- No PDF manual is fully synchronized with the 1.4.3 UI/features; use these release notes and installation guides as the current documentation.

## Assets / 实际附件

- `QQ-ChainScope-1.4.3-Windows-x64-VST3.zip`
- `QQ-ChainScope-1.4.3-Installation-Guide-Chinese.txt`
- `QQ-ChainScope-1.4.3-Installation-Guide-English.txt`
- `QQ-ChainScope-1.4.3-Release-Notes-Bilingual.md`
- `QQ-ChainScope-1.4.3-SHA256SUMS.txt`

QQ ChainScope is proprietary software. Source code is not included in this public repository or Release.

QQ ChainScope 为闭源软件；本公共仓库和 Release 不包含源代码。
