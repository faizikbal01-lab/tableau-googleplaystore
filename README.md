# Google Play Store App Analysis — Tableau Dashboard

## Project Overview

The mobile app economy is one of the fastest-growing digital markets, with millions of apps competing for user attention, downloads, and ratings. This project presents a **Tableau-powered visual analysis** of the **Google Play Store** dataset, covering **10,000+ apps** across 33 categories. The study focuses on understanding what drives app success — from user ratings and install counts to pricing strategy, content classification, and app lifecycle trends.

As a **Business and Data Analyst**, the goal is to translate raw app store metadata into strategic intelligence that can help **app developers, product managers, and market researchers** make informed decisions about app positioning, pricing, and improvement.

---

## Business & Product Objectives

The analysis seeks to provide data-backed answers to the following critical questions:

1. **Category Performance:** Which app categories attract the highest volume of installs and the best user ratings?
2. **Free vs. Paid Strategy:** How does monetization type (Free vs. Paid) affect install counts and average ratings?
3. **Content & Audience:** How are apps distributed across content ratings (Everyone, Teen, Mature 17+), and which categories skew toward specific audiences?
4. **App Lifecycle:** Which apps are "Zombie" apps (not updated in 2+ years) vs. "Active" apps — and what does this mean for quality?
5. **Review Volume & Engagement:** Which apps and categories generate the most user reviews, and what does this reveal about engagement?
6. **Update Recency:** How many apps were updated in 2018, and what does freshness signal about developer activity and user trust?

---

## Dataset Description

The analysis is powered by a single dataset — `googleplaystore.xlsx` — containing **10,359 rows** and **13 columns**:

| Feature | Type | Description |
| --- | --- | --- |
| `App` | String | Name of the application |
| `Category` | String | App category (e.g., GAME, SOCIAL, TOOLS) — 33 unique values |
| `Rating` | String/Float | Average user rating (out of 5.0) |
| `Reviews` | Integer | Total number of user reviews |
| `Size` | String | App size (e.g., "19M", "varies with device") |
| `Installs` | String | Install range bracket (e.g., "10,000+", "1,000,000+") |
| `Type` | String | Free or Paid |
| `Price` | Float | Price in USD (0.0 for free apps) |
| `Content Rating` | String | Target audience (Everyone, Teen, Mature 17+, etc.) |
| `Genres` | String | Detailed genre classification (103 unique values) |
| `Last Updated` | Date | Date the app was last updated on the Play Store |
| `Current Ver` | String | Current version of the app |
| `Android Ver` | String | Minimum Android version required |

---

## Calculated Fields & Methodology

The Tableau workbook includes **custom calculated fields** built to answer deeper analytical questions:

| Calculated Field | Logic |
| --- | --- |
| `avg rating` | `AVG([Rating])` — Average rating across apps |
| `Unique category` | `COUNTD([Category])` — Count of distinct categories |
| `free vs Paid` | Classifies apps as "Free" (Price = 0) or "Paid" |
| `top 5 apps` | Converts `Installs` string to integer for ranking |
| `most installed app` | Numeric install count for identifying top apps |
| `rating less than 4.0` | Flags apps with ratings at or above 4.0 |
| `Average Reviews per App Type` | `AVG([Reviews])` segmented by Free/Paid |
| `Size Numeric` | Converts size strings (e.g., "19M") to float for analysis |
| `Apps Updated in 2018` | Flags apps last updated in 2018 |
| `Installs vs Rating Correlation` | `CORR([Installs],[Rating])` — Correlation analysis |
| `trend of apps` | Classifies apps as **"Active"** or **"Zombie"** (not updated in 2+ years) |
| `Review theme` | Categorizes review content into themes: Technical Issues, Cost, Usability, Positive Experience, Other |
| `Rating whole no.` | `ROUND([Rating], 0)` — Rounded rating for bucketing |

---

## Dashboard Sheets

### Sheet 1 — Category × Content Rating Heatmap
A density heatmap showing the **distribution of apps** across every combination of **Category** (rows) and **Content Rating** (columns). Color intensity reflects the count of apps in each cell, revealing which categories are dominated by "Everyone"-rated apps vs. those with more age-restricted content.

### Sheet 2 — Average Rating by Category
A horizontal bar chart displaying the **average user rating per app category**, enabling quick identification of which categories consistently deliver high-quality experiences and which fall short.

---

## Key Insights (Executive Summary)

- **Dominant Categories:** FAMILY and GAME categories account for the largest share of apps on the Play Store, yet Technology and Communication apps tend to lead in install volume.
- **Rating Plateau:** Most apps cluster between ratings of **3.5 and 4.5**, suggesting a competitive but undifferentiated quality landscape — standing out requires more than just being "good."
- **Free App Dominance:** The vast majority of apps are free, but paid apps tend to have slightly higher ratings, possibly due to higher user intent and lower volume of casual reviewers.
- **Zombie Apps:** A significant portion of apps have not been updated in over 2 years, signaling developer abandonment — a risk factor for users and a competitive opportunity for active developers.
- **Content Skew:** The majority of apps target the "Everyone" content rating, with GAME and ENTERTAINMENT categories showing higher representation of "Teen" and "Mature 17+" rated apps.
- **2018 Update Activity:** Apps updated in 2018 represent a strong signal of developer engagement and are likely to show better ratings and install trends.

---

## Tools & Technologies

- **Tableau Desktop 2025.3** — Dashboard creation, calculated fields, and visual analytics
- **Data Source:** `googleplaystore.xlsx` (connected via Excel Direct)
- **Visualization Types:** Heatmap (density), horizontal bar chart

---

## Repository Structure

```
📁 Google-PlayStore-Tableau-Analysis/
├── Book1.twb                    # Tableau workbook (connect to data source to explore)
├── googleplaystore.xlsx         # Source dataset (place in same directory or reconnect path)
└── README.md
```

---

## How to Open & Use

1. **Clone the Repository:**

```bash
git clone https://github.com/your-username/Google-PlayStore-Tableau-Analysis.git
```

2. **Open the Workbook:**
   - Launch **Tableau Desktop** (version 2025.3 or compatible)
   - Open `Book1.twb`
   - If prompted, reconnect the data source to `googleplaystore.xlsx` on your local machine

3. **Explore the Dashboard:**
   - Navigate between **Sheet 1** (Heatmap) and **Sheet 2** (Avg Rating by Category)
   - Use Tableau's built-in filters and tooltips to drill down into specific categories, content ratings, or app types

---

## Data Source

The **Google Play Store** dataset is a publicly available dataset commonly sourced from [Kaggle](https://www.kaggle.com/datasets/lava18/google-play-store-apps). It represents a snapshot of app metadata scraped from the Play Store and is intended for educational and analytical purposes only.

---
## Recommendations for GitHub Upload

Before publishing this project to GitHub, the following improvements are recommended to maximise usability, reproducibility, and professional quality.

### 1. File Naming & Repository Hygiene

- **Rename `Untitled_Report.pdf`:** This is the most visible file in the repo and its current name signals an unfinished project to any visitor. Rename it to something descriptive before upload — e.g. `google_playstore_dashboard_report.pdf`. This single change has an outsized impact on first impressions.
- **Rename `Book1.twb`:** Tableau's default workbook name carries the same problem. Rename to `google_playstore_analysis.twb` (or `.twbx` — see below) to make the project self-describing in a GitHub file listing.
- **Upgrade `.twb` to `.twbx` (packaged workbook):** A `.twb` file contains only the workbook definition — it does not bundle the data source. Anyone cloning the repo must manually reconnect `googleplaystore.xlsx`. A `.twbx` (packaged workbook) embeds the data extract directly, making the dashboard immediately openable without any reconnection step. Export via Tableau Desktop: *File → Export Packaged Workbook*.
- **Add a `.gitignore`:** Exclude Tableau temporary files and OS artefacts:

  ```
  *.twb~
  *.twbx~
  .DS_Store
  Thumbs.db
  ```

- **Do not commit `googleplaystore.xlsx` if file size is a concern:** The dataset is ~6 MB. If you include it, that's acceptable — but add a `data/README.md` noting its Kaggle source so users know where to re-download it if needed.

### 2. Repository Structure

Reorganise the repo for clarity and professionalism:

```
📁 Google-PlayStore-Dashboard/
├── google_playstore_analysis.twbx       # Packaged Tableau workbook (data embedded)
├── data/
│   └── README.md                        # Kaggle download link + dataset description
├── outputs/
│   ├── google_playstore_dashboard.pdf   # Renamed from Untitled_Report.pdf
│   └── screenshots/
│       ├── page1_summary.png            # PNG export of Page 1
│       └── page2_engagement.png         # PNG export of Page 2
└── README.md
```

### 3. Dashboard & Visual Quality

- **Embed dashboard screenshots in the README:** Tableau `.twbx` files and PDFs cannot be previewed on GitHub. Adding PNG screenshots of both dashboard pages is the single most impactful step for a Tableau portfolio project — visitors immediately see the work without downloading anything:

  ```markdown
  ## Dashboard Preview
  ### Page 1 — Summary Metrics & Audience Breakdown
  ![Page 1](outputs/screenshots/page1_summary.png)

  ### Page 2 — Engagement & Distribution Analysis
  ![Page 2](outputs/screenshots/page2_engagement.png)
  ```

- **Investigate the KPI discrepancy:** Page 1 shows **152 apps** in the KPI card, but the dataset contains 9,660+ apps. This suggests an active filter is narrowing the view significantly. Document what filter is applied (e.g. a specific category or size bracket) in the README and in a visible text annotation on the dashboard itself — otherwise viewers will be confused by the mismatch.
- **Replace the parallel coordinates chart if targeting non-technical audiences:** Parallel coordinates plots are powerful but require explanation. Add a brief caption or tooltip instruction on the dashboard, or consider a grouped bar chart alternative for the top-apps-by-category comparison to make it more immediately readable.
- **Add a dashboard title and subtitle to each page:** Currently the pages are described only in this README. Adding a title (e.g. "Google Play Store — Market Overview") and a one-line subtitle directly on each Tableau page makes the dashboard self-describing when shared as a PDF or screenshot.
- **Clarify the `Top Apps by Installs` list:** The five apps shown (English Grammar Test, Ruler, Period Tracker, Calculator, Call Blocker) are likely filtered to a specific segment — these are not the actual top apps by installs globally on the Play Store (which would be Google Maps, YouTube, etc.). Document the active filter context that produces this list.

### 4. Data Quality & Preparation

- **Note the dataset's known anomalies:** The Google Play Store Kaggle dataset has documented quality issues that affect dashboard outputs:
  - A row where `Category = '1.9'` (a CSV row-misalignment) — verify it is excluded from all visuals.
  - `Rating` values above 5.0 exist in some versions — confirm they are filtered out before computing the 4.19 average.
  - `"Varies with device"` entries in the `Size` column should be excluded from the Size vs. Installs scatter to avoid distorted results.
- **Validate the 4 billion total reviews figure:** A sum of `Reviews` across all apps yielding 4,044,332,969 may reflect duplicate records or apps with artificially inflated review counts. Cross-check against the raw CSV before publishing this as a headline KPI.
- **Document the `Installs` column's bracket format:** Raw values like `"10,000+"` are text strings, not numbers. Note in the README how Tableau handles this column (likely as a dimension, not a measure) and whether any calculated field was created to enable numeric sorting or aggregation.
- **Add a data preparation notes section:** Even a brief paragraph describing any cleaning steps performed (deduplication, null removal, type casting) adds credibility and helps users reproduce your results.

### 5. Ethics, Attribution & Licensing

- **Add a formal dataset citation:**
  > Lavanya M. (2019). *Google Play Store Apps.* Kaggle. https://www.kaggle.com/datasets/lava18/google-play-store-apps
- **Add a dataset age warning:** The Kaggle snapshot was scraped in 2018–2019. App counts, category rankings, install figures, and market share have shifted substantially since then. Add a visible note in the README — and ideally a small text annotation on the dashboard itself — that figures reflect a historical snapshot.
- **Add a `LICENSE` file:** Use **MIT License** for the Tableau workbook and README. Clarify that the license applies to your analytical work only, not to the underlying Google Play Store data.
- **Strengthen the disclaimer:** The current disclaimer is at the bottom of the README. Consider also adding a brief note directly on the Tableau dashboard (e.g. in the footer of each page) so the caveat travels with the PDF export and any screenshots shared independently.

### 6. Analysis Quality Improvements

- **Quantify the install-review gap finding:** The Key Insights section notes that "a small number of breakout apps accumulate disproportionately large review volumes." Strengthen this with a specific figure — e.g. "the top 1% of apps by review count account for X% of all reviews." This turns a qualitative observation into a concrete, citable insight.
- **Add a time-based analysis using `Last Updated`:** The dataset includes `Last Updated` dates. A line chart of app update frequency by year or a bar chart of apps by last-update recency would add a temporal dimension currently absent from both dashboard pages.
- **Add a Paid app deep-dive:** The 7.4% Paid app segment is noted but not explored. A dedicated filter or page section comparing Paid app ratings, review counts, and install volumes by category would give the monetization story much more depth.
- **Consider adding a category-level average rating heatmap:** A heatmap or colour-coded table showing average rating per category is a standard and highly readable addition to any Play Store dashboard — and it directly addresses Business Objective #1 (rating benchmarking by category).

---

## Author

**Mohd Faiz**
- **Role:** Business and Data Analyst
- **GitHub:** [https://github.com/faizikbal01-lab](https://github.com/your-username)

---

*Disclaimer: This analysis is based on a publicly available snapshot of Google Play Store data and is intended for educational and portfolio demonstration purposes only. It is not affiliated with or endorsed by Google.*

