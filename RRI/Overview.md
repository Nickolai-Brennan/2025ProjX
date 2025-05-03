Here is the full **RRI v2025.1 Formula + Version Update** in clean **Markdown format**, followed by a code block version for embedding into GitHub, Notion, or your documentation system.

---

### 📄 MARKDOWN VERSION — `README.md`

```markdown
# ⚾ Reliever Reliability Index (RRI) – Version 2025.1

**Author:** Nick Brennan  
**Platform:** xSTATx Analytics  
**Release:** May 2025  
**Status:** Live ✅

---

## 🧠 What's New in v2025.1

### 🔄 Updated Base Score Formula

```text
Base_Score = 1.10 × (
    0.65 × Pitcher_Status_Score +
    0.15 × Previous_Season_RRI +
    0.25 × Pitcher_Ranker_Tier_Score
)
```

- **Pitcher_Status_Score** is derived from 14-day Avg_LI (Leverage Index)
- **Previous_Season_RRI** is the pitcher’s prior-year RRI score
- **Pitcher_Ranker_Tier_Score** is mapped from custom tier system

---

### 📐 Pitcher Status Scoring (65%)

| Avg_LI Range   | Score | Role Label               |
|----------------|--------|--------------------------|
| ≥ 1.70         | 80     | Closer / Fireman Elite   |
| 1.50 – 1.69    | 75     | High-Leverage Relief     |
| 1.30 – 1.49    | 70     | Setup / HL Arm           |
| 1.10 – 1.29    | 60     | Mid-Relief               |
| 0.90 – 1.09    | 50     | Low-Impact Relief        |
| < 0.90         | 35     | Mop-Up / Blowout Role    |

---

### 🎯 Pitcher Ranker Tier Mapping (25%)

| Tier                              | Emoji | Score |
|-----------------------------------|--------|--------|
| Tier 10 – God Tier                | 🐉     | 100    |
| Tier 9 – Untouchable Elite        | 🔥     | 95     |
| Tier 8 – High-End Stoppers        | 💣     | 85     |
| Tier 7 – Reliable HL Arms         | 🧊     | 75     |
| Tier 6 – Stable Contributors      | 🛠️     | 65     |
| Tier 5 – Mid-Tier Relievers       | ⚙️     | 55     |
| Tier 4 – Inconsistent Arms        | 🧪     | 45     |
| Tier 3 – Low-Impact Mop-Ups       | 🧹     | 35     |
| Tier 2 – Call-Up Watch            | 🔍     | 25     |
| Tier 1 – Inactive / RP-Level      | ⚠️     | 15     |

---

### 📊 RRI Formula Structure

```text
RRI = (
    0.25 × Previous_Season_RRI +
    0.50 × RRI_Current_Season_Score +
    0.25 × RRI_Non_Playing_Score
)
```

---

### 📊 RRI_Current_Season_Score Breakdown

| Category                  | Weight |
|---------------------------|--------|
| Performance Metrics       | 30%    |
| Leverage & Usage          | 20%    |
| Saves & Holds             | 15%    |
| Stuff & Pitching Quality  | 15%    |
| Batted Ball Metrics       | 10%    |
| Clutch & IR Performance   | 10%    |

---

### 🧬 RRI_Non_Playing_Score Breakdown

| Category                  | Weight |
|---------------------------|--------|
| Prospect Status           | 5%     |
| Injury History            | 5%     |
| Team Contention Bonus     | 5%     |
| Trade Rumors (June–July)  | 1%     |
| Role Type Classification  | 5%     |
| Age-Based Scaling         | 4%     |

---

## ✅ Example Output

| Pitcher               | Role Score | Prev RRI | Tier Score | Raw Base | Final Base |
|-----------------------|------------|----------|------------|----------|-------------|
| Mariano Rivera (2008) | 80         | 95       | 100        | 89.75    | 98.73 🔥     |
| Robert Suarez (2025)  | 75         | 68       | 95         | 82.7     | 90.97 💣     |
| Yennier Cano (2025)   | 70         | 75       | 75         | 75.5     | 83.05 🧊     |

---

## 🔗 Export Fields

- `Base_Score_Raw`
- `Base_Score_Final`
- `RRI_Score_Final`
- `Pitcher_Ranker_Tier`
- `Role_Type_Label`

Use for:  
- ✅ WordPress leaderboard  
- 📊 Google Sheets tracker  
- 🧩 Fantasy projections or value modeling
```

---

Would you like this as a downloadable `.md` file or inserted directly into your GitHub wiki as a page?
