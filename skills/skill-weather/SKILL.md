---
name: skill-weather
description: >
  Query weather. Triggers on: 天气, 温度, 下雨, 带伞, 出游, 热不热,
  明天会下雨吗, 周末天气, 出门, weather, temperature, rain, forecast.
---

Extract city name from user message. Ask if missing. Default: brief + today only.

Detail level: no keyword = brief (weather/temp/wind). "详细/detailed" = add humidity, UV, AQI, sunrise/sunset.
Days: no keyword = today. "3天/3 days" = 3 days. "一周/7天/week" = 7 days.

Search `<city> 天气` once.

Output: compact table with weather/temp/wind. Multi-day uses table. NO 24h hourly, NO overview summary, NO AskUserQuestion.

One-line advice. Never invent data.
