Here’s the fully expanded **RRI (Reliever Reliability Index) Guide & README** — structured for GitHub, documentation portals, or WordPress wiki pages. This version improves clarity, modular formatting, and incorporates your extended formulas and scaling notes.

---

# ⚾ **Reliever Reliability Index (RRI) – Full Guide & Formula README**

> **By Nick Brennan – xSTATx | 2025**

---

## 🧠 What is RRI?

The **Reliever Reliability Index (RRI)** is a data science-based model that quantifies the value, consistency, and trustworthiness of MLB relief pitchers. It integrates **real-time usage patterns, sabermetric metrics, player context, and role-based projections** into one unified score. RRI is designed for fantasy analysts, player developers, and front offices who need more than just "saves" and "ERA."

Unlike static stat sheets or outdated bullpen roles, RRI **captures the true impact** of relievers—*when they're used, how they perform, and whether they belong in your circle of trust.*

---

## 💪 Core Pillars of the RRI System

### 1. **Contextual Role Analysis**
- Relievers are scored based on **14-day rolling Average Leverage Index (Avg_LI)**, not fixed titles like "Closer" or "Setup."
- This allows the system to detect *real* usage value, not label-based assumptions.

### 2. **Sabermetric Performance Inputs**
Includes:
- **xERA / SIERA** for ERA projection
- **K/BB (60-day)** ratio for command
- **wOBAA** for contact quality allowed
- **Stuff+, Pitching+, Location+** to measure pitch arsenal and execution

### 3. **Layered Adjustments**
- ✅ **Prospect Bonuses** for hyped call-ups
- ❌ **Injury Penalties** for durability risk
- 📊 **Team Standing Bonuses** for leverage availability
- 🧱 **Role Tiers via Leverage Index**
- ⚠️ **Trade Rumor Penalties** during trade season only

### 4. **Scalable, Visual, Export-Friendly**
- Dashboard-ready outputs with:
  - 🔥 Top 5% Stuff Badge
  - 🎯 Elite K/BB Badge
  - 🧱 Leverage Monster Badge
  - 🚨 Injury Watch Flag
  - 🌟 Prospect Upside Tag

---

## 🧮 Base Role Score by Avg_LI

| Avg_LI Range | Base RRI Score | Role Interpretation |
|--------------|----------------|---------------------|
| ≥ 1.70       | 80             | Elite Closer / Fireman |
| 1.50–1.69    | 75             | High-Leverage Relief |
| 1.30–1.49    | 70             | Setup |
| 1.10–1.29    | 60             | Mid Relief |
| 0.90–1.09    | 50             | Low-Impact Relief |
| < 0.90       | 35             | Mop-Up |

---

## 📊 RRI Formula Overview

```python
RRI = (
    0.25 * RRI_Prior_Year +
    0.50 * RRI_Current_Season +
    0.25 * RRI_Non_Playing_Stats
)
```

### 🔹 Current Season Score (50%)
| Component                     | Weight |
|------------------------------|--------|
| Performance Metrics          | 30%    |
| Leverage & Usage             | 20%    |
| Saves and Holds              | 15%    |
| Stuff & Pitching Quality     | 15%    |
| Batted Ball Metrics          | 10%    |
| Clutch & IR%                 | 10%    |

### 🔸 Non-Playing Score (25%)
| Component                     | Weight |
|------------------------------|--------|
| Prospect Status              | 5%     |
| Injury History               | 5%     |
| Team Contention              | 5%     |
| Trade Rumors (June–Deadline) | 1%     |
| Role Type                    | 5%     |
| Age Sliding Penalty          | 4% (up to -20%) |

---

## 📈 Sample RRI Calculation – *Emmanuel Clase*

| Metric                    | Value           | RRI Impact   |
|--------------------------|------------------|--------------|
| Avg_LI                   | 1.47             | +70 Base     |
| K/BB                     | 7.00             | +7.5         |
| xERA                     | 3.55             | 0            |
| wOBAA Proxy              | High             | -3           |
| Stuff+                   | 128              | +2.0         |
| SVH%                     | 90%              | +5           |
| IL History               | 2 Stints         | -4           |
| Prospect Boost           | Top 100          | +2.5         |
| Trade Rumor              | Active (July)    | -5           |
| Team Bonus               | CLE: 2nd Place   | +2           |

✅ **Final RRI ≈ 79.5**

---

## ⚖️ Detailed Metric Scaling Breakdown

### 🧪 Performance Metrics (30%)

| Stat     | Weight | Scaling Type |
|----------|--------|--------------|
| ERA      | 10%    | Reverse Scaled |
| xFIP     | 10%    | Reverse Scaled |
| WHIP     | 2.5%   | Reverse Scaled |
| BABIP    | 2.5%   | Reverse Scaled |
| K/9      | 2.5%   | Min-Max       |
| BB/9     | 2.5%   | Reverse       |
| K-BB%    | 5%     | Min-Max       |

```python
def scale_stat(series, reverse=False):
    scaled = (series - series.min()) / (series.max() - series.min())
    return 1 - scaled if reverse else scaled
```

---

### ⛽ Leverage + Usage (20–25%)

| Metric           | Weight | Notes                     |
|------------------|--------|---------------------------|
| aLI              | 5%     | High-Leverage Index       |
| pLI              | 1%     | Pressure Index            |
| gmLI             | 3%     | Game-Level Leverage       |
| Clutch           | 4%     | Win probability swings    |
| IR%              | 4%     | Inherited Runners scored  |
| WAR              | 5%     | Contextual efficiency     |

---

### 🏆 Saves + Holds (15%)

- **SV Efficiency** = (SV / Opportunities)
- **Hold Efficiency** = (HLD / Opportunities)
- **Max Bonus:** +5 pts via efficiency

---

### 🧠 Stuff & Pitching Quality (15%)

| Sub-Metric             | Weight |
|------------------------|--------|
| Stuff+, Location+, Pitching+ | 7.5% |
| Plate Discipline (CSW%, etc) | 3.75% |
| Weighted Pitch Value         | 3.75% |
| Top 5% Pitch Flag             | +2   |

---

### 🧱 Batted Ball Profile (10%)

```python
Batted_Ball_Score = (
    0.80 * CSW%_Scaled +
    0.10 * Soft%_Scaled +
    0.10 * HardHit%_Scaled
)
```

---

## 🔍 Non-Playing Metrics (25%)

| Category               | Scoring Method |
|------------------------|----------------|
| Prospect Status        | Top 10: +5 → Org Rank: +1 |
| Injury Field           | +0 to -10      |
| Team Contention        | +4 (1st Place) → -3 (Bottom Tier) |
| Trade Rumors (July)    | -10% to -25% of RRI |
| Age Sliding Scale      | Age 37+: -5% to -20% |

---

## 📌 Areas for Future Expansion

| Idea | Description |
|------|-------------|
| 🧠 Auto-load age & IL history | Pull from MLB + RosterResource |
| 📈 Game Log Graphing | Plot LI and Clutch metrics over time |
| ⚾ Add SVH% Efficiency Column | Actual opps vs. outcomes |
| 🔄 Trade Rumor Feed | Link to MLBTR / FanGraphs |
| 🎯 Add Zone%, 1st Strike% | Improve Command Profiling |
| 🔄 Sync w/ Google Sheets API | Auto-refresh RRI leaderboard |

---

## 🧬 Final Thoughts

The **Reliever Reliability Index** is not a replacement for scouting or traditional metrics—it's an **augmentation layer** that allows you to:

- Detect hidden bullpen gems
- Avoid trap closers
- Track reliever evolution over time
- Quantify “trust” with data

It is the **modern bullpen blueprint**.

---

Would you like this exported into:
- 📄 **Markdown (.md)**?
- 📊 **Google Sheets-linked documentation**?
- 🧩 **WordPress-compatible HTML block**?
- 💻 **API-ready JSON schema**?

Let me know the next format you need!
