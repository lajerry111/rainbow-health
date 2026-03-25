# RainbowHealth Coach

基于 OpenClaw 的减脂增肌抗炎控糖专家教练系统

## Core Architecture

### Five Health Dimensions (V-Score v3.8)
- **Metabolic Foundation** (25%) - Body fat, visceral fat, steps
- **Nutrition Quality** (30%) - Nutritional structure, calorie accuracy, anti-inflammatory ratio
- **Sleep Recovery** (15%) - Deep sleep, sleep efficiency, sleep onset time
- **Exercise Vitality** (15%) - Exercise duration, exercise intensity
- **Stress Management** (15%) - Subjective stress, HRV

### Four Core Modules
1. **Fat Loss** - Calorie management, body fat tracking, metabolic optimization
2. **Muscle Gain** - Protein management, training planning, recovery monitoring
3. **Anti-inflammatory** - Dietary inflammation index, Omega balance, lifestyle
4. **Glucose Control** - CGM monitoring, blood glucose fluctuations, insulin sensitivity

### Hardware Support
- Eight-electrode body composition scale (body composition data)
- Smart bracelet (steps, heart rate, HRV, sleep)
- CGM continuous glucose monitor (real-time glucose curve)

## Skill Directory

```
skills/
├── 00-core/                    # Core infrastructure
├── 01-assessment/              # V-Score assessment system
├── 02-fat-loss/                # Fat loss module
├── 03-muscle-gain/             # Muscle gain module
├── 04-anti-inflammatory/       # Anti-inflammatory module
├── 05-glucose-control/         # Glucose control module
├── 06-daily-coaching/          # Daily coaching
├── 07-tplate/                  # T-plate system
└── 08-reports/                 # Reporting system
```

## License

Proprietary - All rights reserved
