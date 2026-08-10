<div align="center">

# 📖 A-writer-should-do

**六维文学DNA蒸馏** — 从单本图书文本中提取作者理解世界的方式，<br>生成可直接调用的写作指导 Skill，内置反AI检测机制

[![Stars](https://img.shields.io/github/stars/masterball-w/A-writer-should-do?style=flat-square&logo=github&color=yellow)](https://github.com/masterball-w/A-writer-should-do/stargazers)
[![Forks](https://img.shields.io/github/forks/masterball-w/A-writer-should-do?style=flat-square&logo=git&color=orange)](https://github.com/masterball-w/A-writer-should-do/forks)
[![Issues](https://img.shields.io/github/issues/masterball-w/A-writer-should-do?style=flat-square&color=red)](https://github.com/masterball-w/A-writer-should-do/issues)
[![Last Commit](https://img.shields.io/github/last-commit/masterball-w/A-writer-should-do?style=flat-square&logo=git&color=blue)
](https://github.com/masterball-w/A-writer-should-do/commits/main)
[![Repo Size](https://img.shields.io/github/repo-size/masterball-w/A-writer-should-do?style=flat-square&color=green)]()
![Languages](https://img.shields.io/github/languages/count/masterball-w/A-writer-should-do?style=flat-square&color=lightgrey)

![Skill](https://img.shields.io/badge/Skill-Literary%20DNA%20Distillation-orange?style=flat-square)
![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white)
![Markdown](https://img.shields.io/badge/Markdown-000000?style=flat-square&logo=markdown&logoColor=white)
![Anti-AI](https://img.shields.io/badge/Anti--AI-Built--in%20Detection-brightgreen?style=flat-square)
![Instances](https://img.shields.io/badge/Style%20Instances-6-blueviolet?style=flat-square)

</div>

---

## 📢 更新动态：v2.0 六维文学DNA架构重构

> 本次更新是一次**架构级重构**：不增加分析模块，而是合并重叠维度、提高单模块信息密度，让中等上下文模型也能稳定执行全流程，并让蒸馏目标从"像作者说话"升级为"**像作者理解世界**"。

**核心变化**

- **八维 → 六维**：原八个维度文件两两合并为六个文学DNA维度，全部既有规则无损保留，删除的是重复与理论膨胀
- **黑名单去重**：AI典型写法黑名单原先在每个维度文件中重复收录（占近半篇幅），现唯一收录于 `06-generation-editor.md`
- **流水线精简**：删除独立的反AI扫描步骤与独立人格分析步骤，边界声明只执行一次，主干收敛为五步
- **新增两个轻量组件**（不新增模块）：每个子 Skill 顶部增加 ≤500字的 **Literary DNA Summary**（最高优先级参考）与最多5条的 **Common Failure Modes**（错误/原因/修正，防止"像作者但没有文学价值"）

**维度合并对照**

| 原八维 | 新六维 |
|---|---|
| 整体风格与人格底色 | 01 作者精神模型 |
| 主题取向 + 认知价值 | 02 母题与世界观 |
| 谋篇布局 + 行文逻辑 | 03 叙事结构机制 |
| 节奏密度 + 词句习惯 | 04 语言节奏系统 |
| 修辞策略 + 负空间分析 | 05 表达技法与留白 |
| 反AI检测 + 编辑层 + 反模仿伦理 | 06 生成约束与编辑校验 |

**对使用者的影响**

- 旧的 `01-style-personality.md` 等八个维度文件已全部移除，引用旧文件名的流程须改用新文件名
- 6个存量子 Skill（含新入库的 `write-like-lijieren`）均已同步重构，种子文本库与风格化规则完整保留
- 顺带修复：lijieren 黑名单补齐 A11、清除旧版"以原文为模板改写"的违规表述、移除 pha 种子库中违反反模仿伦理的"生成示范"

---

## 📑 目录

- [更新动态](#-更新动态v20-六维文学dna架构重构)
- [概述](#-概述)
- [架构原则](#-架构原则)
- [母子 Skill 界定](#️-母子-skill-界定)
- [子 Skill 实例一览](#-子-skill-实例一览)
- [工作流程](#-工作流程)
- [六维文学DNA结构](#-六维文学dna结构)
- [反AI机制](#️-反ai机制)
- [快速开始](#-快速开始)
- [文件说明](#-文件说明)
- [质量保障](#-质量保障)

---

## ✨ 概述

**A-writer-should-do** 是一个文学风格蒸馏 Skill（母 Skill）：从单本图书文本中蒸馏作者的**六维文学DNA**，将特征转化为可执行的写作规则，输出一套派生写作指导 Skill 文件集（子 Skill）。

与统计词频式的风格提取不同，本 Skill 的蒸馏目标是**作者解释世界的方法**——他如何观察、同情什么、恐惧什么、如何处理痛苦、为什么这样安排叙事。语言习惯只是这套精神模型的外壳。

> 💡 生成的子 Skill 不只让文本"像作者说话"，更重要的是"像作者理解世界"。

## 🧭 架构原则

1. **模块少而密**：六个维度，不再增加。文学特征天然重叠，合并优先于细分——让中等上下文模型也能稳定执行全流程。
2. **文学有效性检验**：任何分析概念必须回答"它能改变最终生成文本吗？"不能直接影响生成质量的，不作为独立模块存在。
3. **像作者理解世界，而非像作者说话**：蒸馏终点是世界观与判断方式，避免"像作者但没有文学价值"的空壳仿写。

## 🏗️ 母子 Skill 界定

| 层级 | 名称 | 角色 | 说明 |
|:---:|---|---|---|
| 🏭 母 Skill | `A-writer-should-do` | 特征蒸馏方法论 | 定义提取原则、五步流水线、六维细则、转换法则、模板与自检清单。是生成子 Skill 的"工厂" |
| 📄 子 Skill | `write-like-{作者}` | 派生写作指导实例 | 由母 Skill 以单本书为输入蒸馏生成，含 Literary DNA Summary、六维规则文件、种子文本库与失败案例，直接用于仿写 |

## 🎨 子 Skill 实例一览

| # | 子 Skill | 蒸馏来源 | 风格定位 |
|:---:|---|---|---|
| 1 | `write-like-pha` | 《人生拒绝清单》（pha 著，程俐 译） | "废柴"自嘲式言说、否定式命题、人生减负哲学 |
| 2 | `write-like-zhouguoping` | 《周国平人生哲思录》 | 冲淡平和的哲理散文、格言-随感交替、思辨翻转 |
| 3 | `write-like-yuhua` | 《我们生活在巨大的差距里》 | 余华散文杂文：平静叙述荒诞、并置对照、日常物承载思想 |
| 4 | `write-like-yuhua-novel` | 《活着》 | 余华小说：冷峻克制、民间口语、白描死亡、拒绝升华 |
| 5 | `write-like-liuzhenyun` | 《一日三秋》 | 刘震云：以笑话写哭、日常物丈量生死、链条对话、绕圈归因 |
| 6 | `write-like-lijieren` | 《死水微澜》 | 李劼人：方志家立场、分层语言、清单式密度、白描不评判 |

> 📌 同一作者的不同文体可分别蒸馏、并存使用（如 `write-like-yuhua` 与 `write-like-yuhua-novel`）：散文任务用散文版，小说任务用小说版。

## 🔄 工作流程

```
输入书籍文本（epub / mobi / azw3 需先经步骤0脚本提取）
    │
    ▼
步骤0  源文本准备（extract_epub / extract_mobi / extract_azw3 →
        {书名}_fulltext.txt 纯正文 + {书名}_toc.txt 索引式目录）
    │
    ▼
步骤1  文本理解（文体判定 / 文本属性 / 边界声明一次完成 / 全局锚定）
    │
    ▼
步骤2  六维文学DNA提取（反AI特征随维度同步识别，不单独扫描）
    │
    ▼
步骤3  原文证据验证（频次≥3 / 降噪排除 / 例证回填）
    │
    ▼
步骤4  生成规则转换（特征→祈使规则 + DNA摘要 + 失败案例 + 种子文本）
    │
    ▼
步骤5  编辑校验（文件集质量自检）
    │
    ▼
输出：write-like-{作者}/  （1个主调度文件 + 6个维度文件）
    │
    ▼
派生 Skill 执行写作任务时，成稿以 {文章标题}.md 保存到当前工作目录
```

## 🧬 六维文学DNA结构

派生 Skill 以文件集形式输出，主 `SKILL.md` 规定执行顺序，六个维度各为独立文件：

| 执行顺序 | 文件 | 维度 | 核心问题 |
|:---:|---|---|---|
| 1 | `01-author-spirit.md` | 作者精神模型 | 作者如何解释世界？（观察方式/同情对象/恐惧对象/情绪底色/叙事距离） |
| 2 | `02-theme-worldview.md` | 母题与世界观 | 作者反复书写什么、回避什么，如何判断人性？ |
| 3 | `03-narrative-mechanism.md` | 叙事结构机制 | 作者为什么这样安排？（开篇/展开/信息隐藏/转折/结尾的动机） |
| 4 | `04-language-rhythm.md` | 语言节奏系统 | 作者什么时候短、什么时候长？（一切节奏规则写成条件式） |
| 5 | `05-expression-and-space.md` | 表达技法与留白 | 作者怎么写，以及刻意不写什么？（意象/比喻/负空间分析） |
| 6 | `06-generation-editor.md` | 生成约束与编辑校验 | 初稿哪里像AI？哪里不像作者？哪里该删？ |

每个子 Skill 的 `SKILL.md` 还包含两个轻量组件：

- **Literary DNA Summary**（≤500字，最高优先级）：作者如何看世界 / 如何选择人物 / 如何处理痛苦 / 核心表达机制 / 生成时最需避免什么
- **Common Failure Modes**（≤5条）：每条按「错误 / 原因 / 修正」三要素组织，防止"像作者但没有文学价值"

维度1-5的规则四类标记：

| 标记 | 规则类型 | 来源 |
|:---:|---|---|
| ✅ | 遵循（硬性规则） | 频次≥3处验证通过的核心特征 |
| ❌ | 避免（排除规则） | 降噪项 |
| 💡 | 可选（局部技法） | 频次不足3次 |
| 🤖 | AI特征规避 | 与本维度直接相关的反AI特征 |

## 🛡️ 反AI机制

| 层级 | 机制 | 说明 |
|:---:|---|---|
| 1️⃣ | 随维度同步识别 | 提取每个维度时按[反AI]识别要点标注对抗AI生成模式的作者特征，不设独立扫描步骤 |
| 2️⃣ | 维度6集中收编 | AI典型写法黑名单（句式A1-A12、用词B1-B8、结构C1-C6、质感D1-D5）只收录于 `06-generation-editor.md`，全文件集无重复收录 |
| 3️⃣ | 编辑校验三问 | 成稿后逐段执行：删除什么 / 哪里应该停顿 / 哪里应该留白 |
| 4️⃣ | 文学真实性检查 | 是否复制作者表面语言 / 是否缺少真实细节 / 是否只有风格没有世界观 / 人物台词真实性 |

> 🔍 黑名单示例：**A11「短直简」速记式描写** — 禁止"照得人脸上发青""把东西攥在手里，攥得发白"这类无过程、无细节、无叙事功能的状态派发；**A12 主题词借壳** — 禁止虚构人物替文章论点说话、配完美金句。

## 🚀 快速开始

### 用母 Skill 蒸馏新书

1. 将 `A-writer-should-do` 目录放置于当前 IDE 的 Skill 目录下
2. 提供单本图书文本；若为 epub / mobi / azw3，先执行 `scripts/` 下对应提取脚本（见 SKILL.md「十一、脚本使用指南」）
3. Skill 自动按五步流水线执行蒸馏（文本理解 → DNA提取 → 证据验证 → 规则转换 → 编辑校验）
4. 最终在 Skill 目录下生成一套 `write-like-{作者}/` 文件集（1主文件 + 6维度文件）

### 用子 Skill 指导仿写

1. 将任一子 Skill（如 `write-like-yuhua-novel`）放置于当前 IDE 的 Skill 目录下
2. 先读主文件的 **Literary DNA Summary**（最高优先级），再按顺序加载维度1→5落实初稿
3. 初稿完成后执行维度6全套校验：黑名单 → 真实性检查 → 编辑三问 → 人写技术 → 叙事逻辑自检 → 反模仿伦理
4. 对照 **Common Failure Modes** 复查，成稿以 `{文章标题}.md` 保存到当前工作目录

## 📁 文件说明

```
A-writer-should-do/
├── SKILL.md              # 母 Skill 完整定义（五步流水线 / 六维细则 / 转换法则 / 模板 / 黑名单 / 自检清单）
├── README.md             # 本说明
├── scripts/              # 配套提取脚本（步骤0：电子书转纯文本）
│   ├── extract_epub.py   # EPUB 提取（纯标准库：正文 + 索引式 TOC）
│   ├── extract_mobi.py   # MOBI 提取（mobi 包解包，回退 calibre）
│   ├── extract_azw3.py   # AZW3 提取（calibre 转 epub，回退 mobi 包）
│   └── _text_clean.py    # 共用清洗模块：去除 style/script/head 等，只保留正文
├── write-like-pha/           # 子 Skill 实例1（基于《人生拒绝清单》）
│   ├── SKILL.md              # 主调度（DNA Summary / 总纲 / 执行顺序 / 失败案例 / 校验清单 / 种子文本库 / 边界说明）
│   ├── 01-author-spirit.md
│   ├── 02-theme-worldview.md
│   ├── 03-narrative-mechanism.md
│   ├── 04-language-rhythm.md
│   ├── 05-expression-and-space.md
│   └── 06-generation-editor.md
├── write-like-zhouguoping/   # 子 Skill 实例2（基于《周国平人生哲思录》，同构6+1文件）
├── write-like-yuhua/         # 子 Skill 实例3（基于《我们生活在巨大的差距里》，同构6+1文件）
├── write-like-yuhua-novel/   # 子 Skill 实例4（基于《活着》，同构6+1文件）
├── write-like-liuzhenyun/    # 子 Skill 实例5（基于《一日三秋》，同构6+1文件）
└── write-like-lijieren/      # 子 Skill 实例6（基于《死水微澜》，同构6+1文件）
```

## 🎯 适用文体

小说、散文、杂文、社科论述、传记等各类文体。纯文本（txt/md）可直接输入；电子书格式由 `scripts/` 下脚本转为纯文本后再进入流水线。母 Skill 内置文体差异化权重指引，自动调整六维提取深度。

## ✅ 质量保障

- **两阶段输出**：先完成内部特征分析报告（含文学核心摘要草稿），再转化为派生 Skill
- **原文证据验证**：频次≥3、降噪排除、例证回填三重验证，无例证的特征不入库
- **两组自检清单**：分析报告自检（10.1）+ 派生文件集自检（10.2）
- **维度6终检**：黑名单逐条校验 + 文学真实性四项 + 编辑三问 + 人写模拟E1-E8 + 叙事逻辑四项 + 反模仿伦理
- **Common Failure Modes**：每个子 Skill 内置最多5条高频失败案例（错误/原因/修正），写作前后各对照一遍

---

<div align="center">

**📖 从一本书，蒸馏一种理解世界的方式。**

如果这个项目对你有帮助，欢迎 ⭐ Star 支持一下

</div>
