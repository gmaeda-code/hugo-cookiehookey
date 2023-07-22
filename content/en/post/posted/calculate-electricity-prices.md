---
title: "Calculating electricity prices"
date: 2022-04-09
categories: [Tech]
tags: [Tips]
description: ""
draft: false
---

## Calculation Formula

```math
Electricity bill = Power consumption (Wattage/watts) / 1000 * Hours of use (Hours) * Electricity rate per kWh (27 yen/kWh)
```

Only Watt is requisite, so find Watt anyway.

>Note:
>   - `Power consumption (Wattage/watts) = Pressure of the electricity (Voltage/volts) * Amount of electricity used (Ampere/amps)` is also acceptable.
>   - For kWh, the standard unit price for electric power consumption set by Home Electric Appliances Fair Trade Conference is 27 yen/kWh (from 2014), [now became 31 yen/kWh in 2022](https://www.eftc.or.jp/qa/?topics=1#qa3). The culculation below is based on 27 yen/kWh.

## Example
### Question

We would like to know the electricity rate for one month when using Raspberry Pi 4 Model B as a server for 24 hours a day.

### Calculation
Since we could not find W, I substituted V and A for W. 
Say they are 5V, 2.5A each. 
Therefore, the formula is

```math
Electricity bill = Power consumption (W) / 1000 * Hours of use(Hours) * Electricity charge per kWh (27 yen/kWh)
Electricity bill = {5(V) * 2.5(A)} / 1000 * {24(Hours) * 30(Days)} * 27 yen/kWh
Electricity bill = {12.5} / 1000 * {720} * 27 yen/kWh
Electricity bill = 243 yen
```

In reality, it depends on the configuration and operating conditions.
