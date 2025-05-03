Here's your **Reliever Reliability Index (RRI)** scoring system rewritten in a structured **SQL-style query format** for each category and provided in **Markdown format** for GitHub, documentation, or developer integration.

---

# 📘 RRI (Reliever Reliability Index) – SQL Formula Queries & Markdown Guide

---

## 🧮 Master Formula

```sql
SELECT
  0.25 * Previous_Season_RRI +
  0.50 * Current_Season_RRI +
  0.25 * Non_Playing_Score AS RRI_Total
```

---

## ⚡ 1. Performance Metrics (30%)

```sql
SELECT
  0.30 * SCALE(ERA, 'min-max', 'reverse') +
  0.20 * SCALE(xFIP, 'min-max', 'reverse') +
  0.20 * SCALE(K_9, 'min-max') +
  0.10 * SCALE(BB_9, 'min-max', 'reverse') +
  0.10 * SCALE(K_pct, 'min-max') +
  0.10 * SCALE(BB_pct, 'min-max', 'reverse') AS Performance_Score
```

---

## 🔁 2. Leverage and Usage Score (22%)

```sql
SELECT
  0.25 * SCALE(aLI, 'min-max') +
  0.20 * SCALE(IS_pct, 'min-max', 'reverse') +
  0.20 * SCALE(Zero_Damage_Rate, 'min-max') +
  0.15 * SCALE(Bhd, 'min-max') +
  0.10 * SCALE(Runner_Entries, 'min-max') +
  0.10 * SCALE(Outs_per_GR, 'min-max') AS Leverage_Usage_Score
```

> Note: This version is based on Baseball-Reference RP data (`aLI`, `IS%`, `0DR`, `Bhd`, `Runr`, `Out/GR`)

---

## 💾 3. Saves and Holds Score (15%)

```sql
SELECT
  0.60 * SCALE(Saves, 'min-max') +
  0.40 * SCALE(Holds, 'min-max') AS Saves_Holds_Score
```

> Optionally adjust for:

* Save % → Include `Save_Opportunities - Blown_Saves`
* Hold % → Penalize by IR%

---

## 🧪 4. Stuff and Pitching Quality Score (15%)

```sql
SELECT
  0.40 * SCALE(Stuff_Plus, 'min-max') +
  0.20 * SCALE(Location_Plus, 'min-max') +
  0.20 * SCALE(Pitching_Plus, 'min-max') +
  0.20 * SCALE(CSW_pct, 'min-max') AS Stuff_Quality_Score
```

> 🔧 Add-ons (if available):

* +2.0 if **Top 5% pitch spin**
* +3.75% → Plate Discipline Score
* +3.75% → Weighted Pitch Value

---

## 🧱 5. Batted Ball Metrics (10%)

```sql
SELECT
  0.80 * SCALE(CSW_pct, 'min-max') +
  0.10 * SCALE(Soft_pct, 'min-max') +
  0.10 * SCALE(HardHit_pct, 'min-max', 'reverse') AS Batted_Ball_Score
```

---

## 🎯 6. Clutch and Inherited Runners (10%)

```sql
SELECT
  0.60 * SCALE(Clutch, 'min-max') +
  0.40 * SCALE(Inherited_Runners_Scored_pct, 'min-max', 'reverse') AS Clutch_IR_Score
```

---

## 🧠 7. Non-Playing Factors (25%)

```sql
SELECT
  0.05 * Prospect_Score +
  0.05 * Injury_Score +
  0.05 * Team_Contention_Score +
  0.01 * Trade_Rumor_Score +
  0.05 * Player_Status_Score +
  SCALE(Age, 'sliding-scale') AS Non_Playing_Score
```

---

## 🔍 Scaling Function Reference

```sql
FUNCTION SCALE(stat_value, method='min-max', reverse=false):
  IF reverse:
    RETURN 1 - ((stat_value - MIN) / (MAX - MIN))
  ELSE:
    RETURN (stat_value - MIN) / (MAX - MIN)
```

---

## 📚 Example Category Weights

| Category                   | Weight   |
| -------------------------- | -------- |
| Performance Metrics        | 30%      |
| Leverage and Usage         | 22%      |
| Saves and Holds            | 15%      |
| Stuff & Pitching Quality   | 15%      |
| Batted Ball Metrics        | 10%      |
| Clutch + Inherited Runners | 10%      |
| Prospect Status            | 5%       |
| Injury Field               | 5%       |
| Team Contention            | 5%       |
| Trade Rumors               | 1%       |
| Player Status Type         | 5%       |
| Age Sliding Scale          | Variable |

---

Would you like this exported as:

* 📄 GitHub README file?
* 📊 Google Sheets formula sheet?
* 🧱 Python class to calculate RRI per pitcher?

Let me know how you'd like to apply or expand this next.
