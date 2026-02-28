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

## Author

**Mohd Faiz**
- **Role:** Business and Data Analyst
- **GitHub:** [https://github.com/faizikbal01-lab](https://github.com/your-username)

---

*Disclaimer: This analysis is based on a publicly available snapshot of Google Play Store data and is intended for educational and portfolio demonstration purposes only. It is not affiliated with or endorsed by Google.*

