# 🌱 STM32智能温室项目 - 开发准备中

> **嵌入式暑期训练实战项目** | 基于STM32F103C8T6  
> **状态**：硬件采购中 | **启动日期**：2024-07-25  
> [![GitHub](https://img.shields.io/badge/Status-准备中-yellow)](https://github.com/yourusername/smart-greenhouse-stm32)

##   项目愿景
通过STM32实现温室环境自动化控制：
1. 土壤干燥 → 自动浇水
2. 温度过高 → 自动通风
3. 光照不足 → 自动补光

**技术亮点**：  
- 多传感器融合（DHT11/BH1750/YL-69）  
- 手机蓝牙远程监控  
- 低功耗设计（待机电流<10mA）

##  📋 硬件清单
| **模块**       | **型号**          | **接口** | **学习计划映射**       |
|----------------|-------------------|----------|------------------------|
| 主控           | STM32F103C8T6     | SWD      | 第一周：环境搭建        |
| 温湿度传感器   | DHT11             | GPIO     | Day 7-9：USART通信      |
| 土壤传感器     | YL-69             | ADC      | Day 10-11：ADC采集      |
| 执行机构       | 5V继电器模块      | GPIO     | Day 1：中断控制         |

##  ️ 开发准备
```bash
# 已确认环境
- Keil MDK V5.37 
- STM32CubeMX V6.11.0
- ST-Link Utility V4.6.0

# 学习资源
[嵌入式学习计划表](/docs/learning_plan.md)
