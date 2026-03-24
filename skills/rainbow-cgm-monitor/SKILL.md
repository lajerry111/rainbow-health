---
name: rainbow-cgm-monitor
description: "动态血糖监测（CGM）数据集成，支持 Dexcom、Freestyle Libre 等主流 CGM 设备，提供实时血糖追踪、趋势分析和个性化控糖建议。Use when the user wants to sync CGM data, analyze glucose trends, or manage diabetes."
version: 1.0.0
user-invocable: true
allowed-tools: Read, Write, Edit, Bash, Grep
metadata: {"openclaw":{"emoji":"💉","category":"device-integration","language":"zh"}}
---

# Rainbow CGM Monitor

动态血糖监测（CGM）数据集成技能，支持主流 CGM 设备数据同步，提供实时血糖追踪、趋势预测和个性化控糖建议。

## Capabilities

### 1. 支持设备

| 设备 | 型号 | 数据频率 | 支持程度 |
|------|------|----------|----------|
| Dexcom | G6, G7 | 5分钟 | ✅ 完整支持 |
| FreeStyle Libre | 2, 3 | 1分钟(Libre3)/15分钟(Libre2) | ✅ 完整支持 |
| Medtronic | Guardian | 5分钟 | ✅ 完整支持 |
| 硅基动感 | 国产CGM | 5分钟 | ✅ 完整支持 |
| 三诺爱看 | 国产CGM | 3分钟 | ✅ 完整支持 |
| 其他设备 | - | - | ⚠️ 需配置 |

### 2. 核心指标

#### 血糖指标
- 当前血糖 (mg/dL 或 mmol/L)
- 血糖趋势箭头（上升/下降速度）
- 血糖波动幅度
- 目标范围内时间 (TIR)

#### 时间范围指标
| 指标 | 范围 | 健康目标 |
|------|------|----------|
| TIR | 70-180 mg/dL (3.9-10.0 mmol/L) | >70% |
| TBR | <70 mg/dL (<3.9 mmol/L) | <4% |
| TAR1 | 180-250 mg/dL (10.0-13.9 mmol/L) | <25% |
| TAR2 | >250 mg/dL (>13.9 mmol/L) | <5% |

#### 变异性指标
- 血糖标准差 (SD)
- 变异系数 (CV)
- 血糖管理指标 (GMI)

### 3. 数据分析

#### 模式识别
- 黎明现象检测
- 餐后血糖峰值分析
- 夜间低血糖检测
- 运动对血糖影响
- 压力/情绪相关性

#### 事件标记
- 用餐记录与血糖关联
- 药物/胰岛素注射
- 运动活动
- 睡眠时段
- 压力事件

## Usage

### 同步 CGM 数据

```
@rainbow-cgm-monitor 同步今天的 CGM 数据
设备：FreeStyle Libre 3
```

### 分析趋势

```
@rainbow-cgm-monitor 分析本周血糖趋势
```

### 餐后分析

```
@rainbow-cgm-monitor 分析今天的餐后血糖
午餐时间：12:30
```

### 生成 AGP 报告

```
@rainbow-cgm-monitor 生成 AGP 动态血糖图谱
时间范围：过去14天
```

## Data Storage

### 文件结构

```
memory/health/cgm/
├── daily/
│   └── cgm-YYYY-MM-DD.md
├── trends/
│   └── cgm-trend-YYYY-MM.md
├── agp/
│   └── agp-report-YYYY-MM.md
└── events/
    └── cgm-events-YYYY-MM-DD.md
```

### 每日数据文件示例

位置：`memory/health/cgm/daily/cgm-2024-03-24.md`

```markdown
# CGM 血糖记录 - 2024-03-24

## 设备信息
- 设备：FreeStyle Libre 3
- 传感器编号：XXX-XXX-XXX
- 已佩戴天数：7/14

## 今日统计
- 平均血糖：128 mg/dL (7.1 mmol/L)
- 血糖范围：78-182 mg/dL (4.3-10.1 mmol/L)
- TIR：82% ✅
- TBR：2% ✅
- TAR：16%
- 标准差：28 mg/dL
- GMI：6.8%

## 时段分析

### 凌晨 (00:00-06:00)
- 平均血糖：95 mg/dL
- 范围：78-112 mg/dL
- 状态：稳定 ✓

### 早晨 (06:00-12:00)
- 平均血糖：142 mg/dL
- 餐后峰值：168 mg/dL @ 07:45
- 状态：轻度黎明现象

### 下午 (12:00-18:00)
- 平均血糖：125 mg/dL
- 餐后峰值：152 mg/dL @ 12:45
- 状态：良好

### 晚上 (18:00-24:00)
- 平均血糖：118 mg/dL
- 餐后峰值：138 mg/dL @ 19:15
- 状态：良好

## 事件标记
| 时间 | 事件 | 血糖变化 |
|------|------|----------|
| 07:00 | 早餐（燕麦+鸡蛋） | 102→168 mg/dL |
| 12:30 | 午餐（糙米饭+鸡胸肉+蔬菜） | 98→152 mg/dL |
| 18:30 | 晚餐（藜麦+鱼+沙拉） | 95→138 mg/dL |
| 14:00 | 快走30分钟 | 145→115 mg/dL ↓ |

## 模式识别
- ⚠️ 轻度黎明现象（早晨血糖偏高）
- ✅ 餐后血糖控制良好
- ✅ 运动降糖效果明显

## 建议
1. 早餐后可考虑轻度活动，降低黎明现象影响
2. 当前控糖策略有效，继续保持
3. 注意下午运动后的低血糖风险
```

## AGP 动态血糖图谱

### 什么是 AGP？

Ambulatory Glucose Profile（动态血糖图谱）是标准化的 CGM 数据可视化方法，展示多天血糖数据的中位数曲线和分布范围。

### AGP 报告内容

1. **概览统计**
   - 平均血糖
   - GMI 估算
   - 变异系数
   - TIR/TBR/TAR 比例

2. **24小时中位数曲线**
   - 第50百分位数（中位数）
   - 第25-75百分位数范围
   - 第10-90百分位数范围

3. **日对比图**
   - 连续多天的血糖曲线

4. **时段统计**
   - 午夜-早上6点
   - 早上6点-中午
   - 中午-晚上6点
   - 晚上6点-午夜

## Alert Configuration

支持自定义血糖预警：

| 预警类型 | 默认阈值 | 说明 |
|----------|----------|------|
| 低血糖 | <70 mg/dL | 立即进食 |
| 即将低血糖 | <80 mg/dL | 警告级别 |
| 高血糖 | >180 mg/dL | 检查饮食/药物 |
| 严重高血糖 | >250 mg/dL | 紧急处理 |
| 上升过快 | >2 mg/dL/min | 可能即将高血糖 |
| 下降过快 | <-2 mg/dL/min | 可能即将低血糖 |

## Integration

支持与其他技能联动：

- `rainbow-meal-photo-scorer`：分析餐食对血糖的影响
- `rainbow-smart-bracelet`：关联运动与血糖数据
- `rainbow-xiaohongshu-creator`：生成控糖日记内容
- `diabetes-control-hub`：全面糖尿病管理

## Data Import Methods

1. **Libre 官方 App 导出**
   - Libre 3 App → 报告 → 导出 CSV

2. **Dexcom 官方导出**
   - Dexcom Clarity → 数据导出

3. **第三方平台**
   - Nightscout 集成
   - Tidepool 同步

## Clinical Targets

参考 ADA 2024 标准：

| 指标 | 目标值 |
|------|--------|
| TIR (70-180 mg/dL) | >70% |
| TBR (<70 mg/dL) | <4% |
| TBR (<54 mg/dL) | <1% |
| TAR (>180 mg/dL) | <25% |
| TAR (>250 mg/dL) | <5% |
| CV | <36% |
| GMI | <7% |

## Notes

- CGM 数据延迟：一般 5-15 分钟
- 指尖血糖校准：建议每日至少1次
- 传感器更换期：最后24小时数据可能不稳定
- 药物影响：某些药物可能影响 CGM 准确性
- 剧烈运动：可能导致 CGM 读数临时不准

## Safety Disclaimer

本技能仅用于数据记录和分析，不能替代医疗建议。血糖异常时请咨询医生，紧急情况请立即就医。
