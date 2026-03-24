---
name: rainbow-body-composition-scale
description: "自动获取彩虹生活体脂秤数据，同步体重、体脂率、BMI、肌肉量、内脏脂肪、骨量、水分等多维度健康指标，支持趋势分析和健康建议。Use when the user wants to sync body composition data from Rainbow Life smart scale or track body metrics over time."
version: 1.0.0
user-invocable: true
allowed-tools: Read, Write, Edit, Bash, WebFetch
metadata: {"openclaw":{"emoji":"⚖️","category":"device-integration","language":"zh"}}
---

# Rainbow Body Composition Scale Integration

自动获取彩虹生活体脂秤测量数据，同步多维度身体成分指标，进行趋势分析并提供个性化健康建议。

## Capabilities

### 1. 体脂秤数据自动同步

从彩虹生活体脂秤 API 获取最新测量数据：

| 指标 | 单位 | 说明 |
|------|------|------|
| weight_kg | kg | 体重 |
| body_fat_pct | % | 体脂率 |
| bmi | - | 身体质量指数 |
| muscle_mass_kg | kg | 肌肉量 |
| visceral_fat_level | 1-30 | 内脏脂肪等级 |
| bone_mass_kg | kg | 骨量 |
| water_pct | % | 身体水分率 |
| basal_metabolism | kcal | 基础代谢率 |
| protein_pct | % | 蛋白质率 |
| measurement_time | ISO 8601 | 测量时间 |

### 2. 数据记录与追踪

自动记录测量数据：

1. 将数据保存到 `memory/health/body-composition/` 目录
2. 按日期创建文件：`body-composition-YYYY-MM-DD.md`
3. 维护纵向追踪文件：`body-composition-history.md`
4. 计算与上次测量的变化值

### 3. 指标解读与分类

根据标准范围对各项指标进行分类：

**体脂率分类（中国标准）**
| 类别 | 男性 | 女性 |
|------|------|------|
| 偏瘦 | < 10% | < 20% |
| 标准 | 10-20% | 20-30% |
| 偏高 | 20-25% | 30-35% |
| 高 | > 25% | > 35% |

**BMI 分类**
| 类别 | BMI 范围 |
|------|----------|
| 偏瘦 | < 18.5 |
| 标准 | 18.5-23.9 |
| 超重 | 24-27.9 |
| 肥胖 | ≥ 28 |

### 4. 趋势分析

- 对比上次测量变化
- 7 天、30 天趋势分析
- 生成可视化图表（ASCII 或调用数据可视化工具）

## Usage

### 自动获取最新数据

```
@rainbow-body-composition-scale 获取最新体脂数据
```

### 查看历史趋势

```
@rainbow-body-composition-scale 分析近30天体脂趋势
```

### 生成健康报告

```
@rainbow-body-composition-scale 生成本周身体成分报告
```

## Data Storage

### Daily Log 文件结构

位置：`memory/health/body-composition/body-composition-YYYY-MM-DD.md`

```markdown
# 身体成分测量 - 2024-03-24

## 测量数据
- 测量时间: 2024-03-24T08:30:00+08:00
- 体重: 72.5 kg
- 体脂率: 18.5%
- BMI: 23.2
- 肌肉量: 54.2 kg
- 内脏脂肪: 8 级
- 骨量: 3.1 kg
- 水分率: 55.3%
- 基础代谢: 1620 kcal
- 蛋白质率: 16.8%

## 与上次对比
- 体重变化: -0.3 kg ↓
- 体脂率变化: -0.2% ↓
- BMI变化: -0.1 ↓

## 状态评估
- 体重: 标准范围内 ✓
- 体脂率: 标准范围 ✓
- BMI: 标准范围 ✓

## 建议
1. 继续保持规律运动
2. 注意蛋白质摄入，维持肌肉量
3. 内脏脂肪处于健康水平，继续保持
```

### 历史追踪文件

位置：`memory/health/body-composition/body-composition-history.md`

包含所有测量的汇总数据，用于长期趋势分析。

## API Configuration

需要在环境变量或配置文件中设置：

```bash
RAINBOW_SCALE_API_KEY=your_api_key
RAINBOW_SCALE_USER_ID=your_user_id
RAINBOW_SCALE_DEVICE_ID=your_device_id
```

## Notes

- 首次使用需要配置 API 凭证
- 建议每天同一时间测量（如早晨空腹）
- 数据自动同步到本地健康记忆系统
- 支持与其他技能（如营养分析、运动追踪）联动
