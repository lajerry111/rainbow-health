---
name: rainbow-smart-bracelet
description: "智能手环数据集成，同步心率、步数、睡眠、运动、血氧等数据，支持多品牌手环数据接入和趋势分析。Use when the user wants to sync smart bracelet/fitness tracker data or analyze wearable device metrics."
version: 1.0.0
user-invocable: true
allowed-tools: Read, Write, Edit, Bash
metadata: {"openclaw":{"emoji":"⌚","category":"device-integration","language":"zh"}}
---

# Rainbow Smart Bracelet Integration

智能手环数据集成技能，支持多品牌手环/智能手表数据同步，包括日常活动、心率、睡眠、运动等多维度健康数据。

## Capabilities

### 1. 支持设备

| 品牌 | 数据类型 | 支持程度 |
|------|----------|----------|
| 小米手环 | 步数、心率、睡眠、运动 | ✅ 完整支持 |
| Apple Watch | 活动、心率、睡眠、血氧 | ✅ 完整支持 |
| 华为手环 | 步数、心率、睡眠、运动 | ✅ 完整支持 |
| Garmin | 运动、心率、血氧、睡眠 | ✅ 完整支持 |
| Fitbit | 活动、心率、睡眠 | ✅ 完整支持 |
| 其他品牌 | 基础数据 | ⚠️ 需配置 |

### 2. 数据类型

#### 日常活动数据
- 步数 (steps)
- 距离 (distance_m)
- 消耗热量 (calories_kcal)
- 活跃分钟数 (active_minutes)
- 站立/活动时间

#### 心率数据
- 静息心率 (resting_hr)
- 平均心率 (avg_hr)
- 最大心率 (max_hr)
- 最小心率 (min_hr)
- 心率变异性 HRV

#### 睡眠数据
- 总睡眠时长 (total_sleep_min)
- 深睡时长 (deep_sleep_min)
- 浅睡时长 (light_sleep_min)
- REM 睡眠时长 (rem_sleep_min)
- 清醒次数 (awakenings)
- 睡眠效率 (sleep_efficiency_pct)

#### 运动数据
- 运动类型
- 运动时长
- 消耗热量
- 平均心率
- 运动强度区间
- GPS 轨迹（如支持）

#### 血氧数据
- SpO2 平均水平
- 最低 SpO2
- 测量次数

## Usage

### 同步今日数据

```
@rainbow-smart-bracelet 同步今天的数据
设备：小米手环8
```

### 查看趋势

```
@rainbow-smart-bracelet 分析本周睡眠趋势
```

### 生成报告

```
@rainbow-smart-bracelet 生成本周运动报告
```

## Data Storage

### 文件结构

```
memory/health/smart-bracelet/
├── daily/
│   ├── steps-YYYY-MM-DD.md
│   ├── heart-rate-YYYY-MM-DD.md
│   ├── sleep-YYYY-MM-DD.md
│   └── exercise-YYYY-MM-DD.md
├── trends/
│   ├── steps-trend.md
│   ├── sleep-trend.md
│   └── heart-rate-trend.md
└── summary/
    └── weekly-report-YYYY-WXX.md
```

### 每日数据文件示例

位置：`memory/health/smart-bracelet/daily/steps-2024-03-24.md`

```markdown
# 步数记录 - 2024-03-24

## 设备信息
- 设备：小米手环 8
- 同步时间：2024-03-24 23:45

## 今日数据
- 总步数：8,524
- 目标完成度：85%
- 距离：6.2 km
- 消耗热量：342 kcal
- 活跃分钟数：45 min

## 时段分布
- 00:00-06:00：0 步
- 06:00-12:00：2,150 步
- 12:00-18:00：4,820 步
- 18:00-24:00：1,554 步

## 周对比
- vs 上周同日：+12%
- vs 周平均：+8%

## 备注
- 下午有快走30分钟
```

## Analysis Features

### 1. 步数分析

- 目标达成率
- 时段分布分析
- 周/月趋势对比
- 久坐提醒统计

### 2. 心率分析

- 静息心率趋势
- 心率区间分布
- 异常心率检测
- HRV 压力评估

### 3. 睡眠分析

- 睡眠效率评分
- 睡眠阶段分布
- 入睡/起床时间规律
- 睡眠质量趋势

### 4. 运动分析

- 运动类型分布
- 强度区间统计
- 恢复时间评估
- 训练负荷追踪

## Integration

支持与其他技能联动：

- `rainbow-body-composition-scale`：结合体重变化分析运动效果
- `rainbow-meal-photo-scorer`：分析饮食对睡眠的影响
- `rainbow-xiaohongshu-creator`：生成运动打卡内容

## Configuration

支持多种数据导入方式：

1. **API 自动同步**（需设备支持开放 API）
2. **APP 导出文件导入**（小米运动、Apple Health、华为健康等）
3. **手动输入**（作为备选方案）

## Notes

- 不同品牌设备数据精度有差异
- 首次使用建议导入历史数据建立基线
- 睡眠数据建议在起床后同步（最准确）
- 心率异常数据会触发健康提醒
