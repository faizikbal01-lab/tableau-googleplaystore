# Google Play Store App Analysis — Tableau Dashboard

# 📱 Google Play Store — Tableau Market Analysis

A Tableau dashboard built on 10,841 Google Play Store app records, analyzing market trends across ratings, installs, pricing, categories, and content ratings — designed to help developers and product teams identify where the market opportunities are.

---

## 📋 Dataset at a Glance

| Detail | Info |
|---|---|
| Tool | Tableau Desktop / Tableau Public |
| Source File | `googleplaystoretableau.xlsx` |
| Sheet | `googleplaystore` |
| Rows | 10,841 apps |
| Columns | 13 |

**Columns available for analysis:**

| Column | Type | Notes |
|---|---|---|
| `App` | Text | App name |
| `Category` | Text | 34 unique categories (e.g. ART_AND_DESIGN, GAME) |
| `Rating` | Decimal | Range 1.0–5.0 (contains nulls & outliers) |
| `Reviews` | Integer | Review count per app |
| `Size` | Text | Mixed format — `19M`, `512k`, `Varies with device` |
| `Installs` | Text | String format — `10,000+`, `500,000+` |
| `Type` | Text | `Free` or `Paid` |
| `Price` | Decimal | 0 for free; up to $400 for paid |
| `Content Rating` | Text | Everyone / Teen / Mature 17+ / Adults only 18+ |
| `Genres` | Text | Sub-genre; some apps have multiple (`;` separated) |
| `Last Updated` | Date | Last app update date |
| `Current Ver` | Text | App version string |
| `Android Ver` | Text | Minimum Android version required |

---

## ⚠️ Analyst Notes — Read Before Building

> These are real data quality issues you'll hit immediately in Tableau:

- **`Rating` has outliers** — max value is `19.0` which is invalid; filter to `Rating <= 5.0` before any rating visual
- **`Rating` has nulls** — 1,474 apps have no rating; exclude nulls or handle separately in calculated fields
- **`Size` is a raw string** — `19M`, `512k`, `Varies with device` — create a calculated field to convert to numeric MB before aggregating
- **`Installs` is a string** — `"10,000+"` cannot be summed directly; strip `+` and `,` using a calculated field
- **`Category = '1.9'`** — one anomaly row where category is a version number; exclude via filter
- **`Type` contains `'NaN'`** — 1 row; filter it out in your Free vs. Paid views
- **Free apps: 10,040 | Paid apps: 800** — heavily imbalanced; note this in any Free vs. Paid comparison

---

## 🗂️ Project Structure

```
Google_Play_Tableau/
│
├── googleplaystoretableau.xlsx      # Source dataset (connect in Tableau)
├── google_play_analysis.twbx        # Tableau packaged workbook  ← add this
└── README.md
```

> 💡 Save your Tableau file as a **Packaged Workbook (`.twbx`)** — it bundles the data and dashboard together so anyone can open it without needing the `.xlsx` separately.

---

## ⚙️ Requirements

- **Tableau Desktop** (paid) — [Download trial](https://www.tableau.com/products/desktop)
- **OR Tableau Public** (free) — [Download here](https://public.tableau.com/app/discover)
  - Note: Tableau Public cannot save locally; publish to Tableau Public profile instead

---

## 🚀 Getting Started

**1. Clone the repository**
```bash
git clone https://github.com/your-username/google-play-tableau.git
cd google-play-tableau
```

**5. Publish to Tableau Public (optional)**

- **Server → Tableau Public → Save to Tableau Public**
- Copy the public link and paste it in this README for stakeholders

---

## 💡 Suggested Dashboard Pages

| Page | Key Visuals |
|---|---|
| **Overview** | KPI cards — total apps, avg rating, % free, top category |
| **Category Analysis** | Bar chart — app count & avg rating by category |
| **Installs & Revenue** | Treemap — installs by category; scatter — price vs. installs |
| **Free vs. Paid** | Side-by-side bar — ratings & reviews by type |
| **Content & Audience** | Donut — content rating distribution; filter by category |
| **Trends** | Line chart — apps updated over time by category |

---

## 📌 Recommendations for Improvement

- [ ] **Save as `.twbx`** (packaged workbook) and commit it — right now anyone cloning only gets the raw data with no dashboard
- [ ] **Add a Tableau Public link** to this README — the fastest way for employers to see your work without downloading anything
- [ ] **Fix the `Rating > 5.0` outlier** at the data source level so it doesn't silently skew every average
- [ ] **Build a parameter** to let viewers toggle between Free and Paid apps across all charts simultaneously
- [ ] **Add a Top 10 Apps by Installs** bar chart — it's the most compelling visual for this dataset
- [ ] **Use `Last Updated`** to add a time dimension — showing which categories are most actively maintained is a unique insight most analysts skip
- [ ] **Normalize `Genres`** — some apps have two genres separated by `;`; splitting these unlocks more granular genre-level analysis

---

---

## Author

**Mohd Faiz**
- **Role:** Business and Data Analyst
- **GitHub:** [https://github.com/faizikbal01-lab](https://github.com/your-username)

---

*Disclaimer: This analysis is based on a publicly available snapshot of Google Play Store data and is intended for educational and portfolio demonstration purposes only. It is not affiliated with or endorsed by Google.*

