# 🌈 Rainbow Health

### 228+ 个 AI 健康技能，适用于 Claude Code

![Skills](https://img.shields.io/badge/skills-228+-blue) ![License](https://img.shields.io/badge/license-Proprietary-red)

**完全原创的健康 AI 技能库**

从血压追踪到智能设备集成——全面的健康智能，为你的 AI 助手赋能。

---

## 什么是 Rainbow Health？

Rainbow Health 是一个完全原创的健康 AI 技能库，专为 Claude Code 设计。涵盖智能设备集成、社交化健康管理和视觉 AI 等创新功能。

Rainbow Health 建立在四大支柱之上：

1. **健康记忆系统** —— 在 `memory/health/` 下进行每日健康追踪，在 `~/.claude/patients/` 下维护结构化的临床病历档案。你的数据以纯 Markdown 文件形式存储在本地，由 git 版本控制，完全由你掌控。
2. **模块化技能** —— 228+ 个独立的 `SKILL.md` 文件，每个文件定义自己的提示词、工具和数据格式。按需引入，自由编辑，无限扩展。
3. **智能设备集成** —— 体脂秤、智能手环、CGM 动态血糖监测等设备的无缝数据接入
4. **社交健康内容** —— 生成适合小红书等社交平台分享的健康内容

### 为什么选择 Rainbow Health？

| 特性       | 通用健康应用         | Rainbow Health                          |
| ---------- | -------------------- | --------------------------------------- |
| 数据归属   | 云端 / 厂商锁定     | 本地文件——数据完全属于你                |
| 可定制性   | 固定功能             | 可编辑任何 `SKILL.md`                   |
| 临床深度   | 消费级               | 研究级（PubMed、ClinVar、GWAS）         |
| 集成能力   | 各自孤立             | 技能通过 health-memory 互联互通         |
| AI 模型    | 单一供应商           | 通过 Claude Code 支持任意模型           |
| **智能设备** | 有限支持           | **体脂秤、手环、CGM 全面支持**          |
| **视觉 AI**  | 无照片分析         | **餐食照片营养评分**                    |
| **社交内容** | 通用报告           | **小红书风格健康分享**                  |

---

## 核心架构

### 五大健康维度（V-Score v3.8）
- **代谢基础** (25%) - 体脂率、内脏脂肪、步数
- **营养质量** (30%) - 营养结构、热量准确性、抗炎比例
- **睡眠恢复** (15%) - 深度睡眠、睡眠效率、入睡时间
- **运动活力** (15%) - 运动时长、运动强度
- **压力管理** (15%) - 主观压力、HRV

### 四大核心模块
1. **减脂** - 热量管理、体脂追踪、代谢优化
2. **增肌** - 蛋白质管理、训练规划、恢复监控
3. **抗炎** - 饮食炎症指数、Omega平衡、生活方式
4. **控糖** - CGM监测、血糖波动、胰岛素敏感

---

## 安装

### 方式 A —— Git Clone（推荐）

```bash
# 克隆到 Claude Code 共享技能目录
git clone https://github.com/lajerry111/rainbow-health.git ~/.claude/skills/rainbow-health

# 或克隆到工作区
git clone https://github.com/lajerry111/rainbow-health.git ./skills/rainbow-health
```

### 方式 B —— 按需挑选

```bash
# 只复制你需要的技能
cp -r rainbow-health/skills/body-composition-scale ~/.claude/skills/
cp -r rainbow-health/skills/meal-scoring ~/.claude/skills/
```

无需构建步骤，无需依赖，无需配置向导。Claude Code 会自动发现技能目录中的 `SKILL.md` 文件。

---

## 技能目录

```
skills/
├── 00-core/                    # 核心基础设施
├── 01-assessment/              # V-Score评估体系
├── 02-fat-loss/                # 减脂模块
├── 03-muscle-gain/             # 增肌模块
├── 04-anti-inflammatory/       # 抗炎模块
├── 05-glucose-control/         # 控糖模块
├── 06-daily-coaching/          # 日常教练
├── 07-tplate/                  # T型餐盘系统
└── 08-reports/                 # 报告系统
```

---

## 技能概览

| #  | 分类                                                                     | 数量 | 亮点                                                                                          |
| -- | ------------------------------------------------------------------------ | ---- | --------------------------------------------------------------------------------------------- |
| 1  | [健康记忆与基础设施](#1-健康记忆与基础设施)                              | 2    | `health-memory`、`medical-record-organizer`——所有技能的统一数据层                            |
| 2  | [场景应用](#2-场景应用)                                                  | 7    | `diabetes-control-hub`、`hypertension-daily-copilot`、`mental-wellness-companion`             |
| 3  | [每日健康追踪](#3-每日健康追踪)                                          | 23   | `blood-pressure-tracker`、`sleep-analyzer`、`wearable-analysis-agent`、`weekly-health-digest` |
| 4  | [心理健康与危机干预](#4-心理健康与危机干预)                              | 12   | `crisis-detection-intervention-ai`、`adhd-daily-planner`、`grief-companion`                   |
| 5  | [慢性病与治疗管理](#5-慢性病与治疗管理)                                  | 10   | `chemo-side-effect-tracker`、`medication-reminder`、`post-surgery-recovery`                   |
| 6  | [生物医学数据库](#6-生物医学数据库)                                      | 23   | `pubmed-database`、`clinvar-database`、`kegg-database`、`uniprot-database`                    |
| 7  | [药理学与药物安全](#7-药理学与药物安全)                                  | 9    | `drug-interaction-checker`、`drug-label-lookup`、`drugbank-database`                          |
| 8  | [临床研究与试验](#8-临床研究与试验)                                      | 7    | `trial-eligibility-agent`、`clinical-trial-protocol-skill`、`clinical-diagnostic-reasoning`   |
| 9  | [基因组学与变异解读](#9-基因组学与变异解读)                              | 14   | `variant-interpretation-acmg`、`gwas-lookup`、`gwas-prs`                                      |
| 10 | [药物基因组学](#10-药物基因组学)                                         | 4    | `pharmgx-reporter`、`nutriggx_advisor`、`pharmacogenomics-agent`                               |
| 11 | [肿瘤学与精准医疗](#11-肿瘤学与精准医疗)                                | 13   | `tumor-heterogeneity-agent`、`digital-twin-clinical-agent`、`hrd-analysis-agent`              |
| 12 | [血液学与血液疾病](#12-血液学与血液疾病)                                 | 8    | `chip-clonal-hematopoiesis-agent`、`mpn-progression-monitor-agent`、`myeloma-mrd-agent`       |
| 13 | [免疫信息学](#13-免疫信息学)                                             | 4    | `bio-immunoinformatics-neoantigen-prediction`、`bio-immunoinformatics-mhc-binding-prediction` |
| 14 | [液体活检与 ctDNA](#14-液体活检与-ctdna)                                 | 8    | `bio-ctdna-mutation-detection`、`mrd-edge-detection-agent`、`liquid-biopsy-analytics-agent`   |
| 15 | [ToolUniverse 套件](#15-tooluniverse-套件)                               | 27   | 涵盖数据库、分析和报告的综合多工具研究工作流                                                  |
| 16 | [医学 NLP 与报告](#16-医学-nlp-与报告)                                   | 13   | `clinical-note-summarization`、`radgpt-radiology-reporter`、`checkup-report-interpreter`      |
| 17 | [科研与文献](#17-科研与文献)                                             | 11   | `literature-review`、`deep-research`、`pubmed-search`、`knowledge-synthesis`                  |
| 18 | [数据科学与可视化](#18-数据科学与可视化)                                 | 4    | `statistical-analysis`、`data-visualization-biomedical`、`exploratory-data-analysis`          |
| 19 | [综合健康与生活方式](#19-综合健康与生活方式)                             | 19   | `tcm-constitution-analyzer`、`travel-health-analyzer`、`food-database-query`                  |
| 20 | [工具与文档处理](#20-工具与文档处理)                                     | 5    | `markitdown`、`pdf-processing-pro`、`medical-research-toolkit`                                |
| 21 | [🌈 Rainbow 专属](#21-rainbow-专属智能设备--社交)                       | **6**| **体脂秤集成、餐食照片评分、小红书创作、智能手环、CGM监测**                                   |

**共计：228+ 个技能**

---

## 🌈 Rainbow 专属功能亮点

### 智能设备集成

#### 体脂秤集成 (`body-composition-scale`)
- 自动同步彩虹生活体脂秤数据
- 15项身体成分指标追踪
- 趋势分析和健康建议

#### 智能手环集成 (`smart-bracelet`)
- 支持小米、Apple Watch、华为、Garmin 等品牌
- 步数、心率、睡眠、运动数据同步
- 多维度健康分析

#### CGM 动态血糖监测 (`cgm-monitor`)
- 支持 Dexcom、FreeStyle Libre、硅基动感等设备
- 实时血糖追踪和趋势分析
- AGP 动态血糖图谱生成

### AI 视觉与内容创作

#### 餐食照片评分 (`meal-scoring`)
- 5维度营养评分（控糖、营养、抗炎、热量、多样性）
- AI 视觉分析食物成分
- 个性化健康建议

#### 小红书内容创作 (`xiaohongshu-creator`)
- 健康餐分享文案
- 体重里程碑打卡
- 产品种草内容
- 运动打卡记录

---

## 示例使用场景

### 场景 1: 晨起体重记录

```
用户: 获取今天的体脂数据
AI: 📊 今天早晨 7:30 的测量数据：
    体重: 68.5kg (-0.3kg↓)
    体脂率: 22.5% (-0.2%↓)
    肌肉量: 52.1kg (+0.1kg↑)
    BMI: 22.8 (标准范围)

    周趋势：本周体重下降 0.8kg，体脂下降 0.5%
    继续保持！💪
```

### 场景 2: 餐食分析

```
用户: [上传午餐照片]
用户: 分析这顿饭的营养
AI: 📸 餐食分析报告：

    识别食物：烤鸡胸肉、糙米饭、西兰花、胡萝卜

    📊 五维评分：
    🍬 控糖: 18/20 | 🥗 营养: 19/20 | 🔥 抗炎: 17/20
    ⚖️ 热量: 16/20 | 🌈 多样性: 15/20

    🏆 总分：85分 - 黄金级健康餐！

    💡 建议：可增加一种绿叶蔬菜，营养更均衡

    📱 需要我生成小红书分享文案吗？
```

### 场景 3: 小红书内容生成

```
用户: 帮我生成今天的减脂打卡文案
AI: 📕 小红书文案：

    【标题】85分黄金午餐！这样吃真的太满足了🥗

    【正文】
    今天的午餐必须记录下来！
    五维评分85分，黄金级认证！💎
    ...

    【标签】#减脂餐 #健康午餐 #抗炎饮食
```

---

## 健康记忆系统

所有 Rainbow Health 技能共享统一的 `memory/health/` 存储结构：

```
memory/health/
├── _health-profile.md              # 长期健康基线
├── _preferences.md                 # 用户偏好设置
├── body-composition/               # 🌈 体脂秤数据
├── cgm/                            # 🌈 动态血糖监测数据
├── meal-scores/                    # 🌈 餐食营养评分记录
├── smart-bracelet/                 # 🌈 智能手环数据
├── blood-pressure/
├── blood-glucose/
├── weight/
├── sleep/
├── nutrition/
├── exercise/
├── symptoms/
├── medications/
├── lab-results/
├── imaging/
├── genetics/
├── mental-health/
└── patients/                       # 患者模式下的临床病历
```

---

## 许可证

Proprietary - 完全自有版权

---

<div align="center">

Made with 🌈 by Rainbow Health Team

</div>
