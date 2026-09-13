from pathlib import Path
import fitz, shutil, zipfile, textwrap

src = Path("/mnt/data/Finlatics_presentation.pdf")
repo = Path("/mnt/data/finlatics-youtube-data-science")
assets = repo / "assets"
docs = repo / "docs"
assets.mkdir(parents=True, exist_ok=True)
docs.mkdir(parents=True, exist_ok=True)

# Copy the source presentation into the repo.
shutil.copy2(src, docs / "Finlatics_presentation.pdf")

# Render every presentation page as a GitHub-friendly PNG.
doc = fitz.open(src)
for i, page in enumerate(doc, start=1):
    pix = page.get_pixmap(matrix=fitz.Matrix(1.5, 1.5), alpha=False)
    pix.save(assets / f"slide-{i:02d}.png")

readme = r"""# 📊 Global YouTube Statistics — Data Science Analysis

> A data science project analyzing global YouTube channel statistics to identify patterns in subscribers, views, uploads, channel categories, geography, earnings, subscriber growth, and channel creation trends.

**Project report:** Chaitanya Patil  
**Institution:** Indian Institute of Technology Jodhpur  
**Project:** Finlatics Data Science  
**Primary dataset:** `Global Youtube Statistics.csv`  
**Analysis environment:** Google Colab

---

## 📌 Project Overview

This project analyzes a global YouTube statistics dataset using Python-based data science techniques.

The main objective is to understand **trends, patterns, and insights in the YouTube ecosystem**, with a focus on:

- Influential YouTube channels and subscriber counts
- Video views and subscriber relationships
- Average uploads across content categories
- Geographic distribution of YouTube channels
- Channel-type distribution across categories
- Monthly and yearly earnings
- Recent subscriber growth
- Outliers in yearly earnings
- Channel creation trends over time

The work was developed in **Google Colab**, using common Python data-analysis libraries.

---

## 🎯 Objectives

1. Explore and preprocess global YouTube channel data.
2. Handle duplicate and missing records.
3. Compare the largest YouTube channels by subscribers.
4. Identify categories with high average subscriber counts.
5. Study upload frequency by category.
6. Examine countries with the highest number of channels.
7. Analyze channel types across categories.
8. Compare subscribers with video views.
9. Investigate monthly and yearly earnings.
10. Examine recent subscriber growth.
11. Identify outliers in yearly earnings.
12. Analyze the trend of channel creation over the years.

---

## 🧰 Tools & Technologies

| Tool / Library | Purpose |
|---|---|
| **Python** | Data analysis and visualization |
| **Pandas** | Data loading, cleaning, aggregation and tabular analysis |
| **NumPy** | Numerical operations |
| **Matplotlib** | Data visualization |
| **Seaborn** | Statistical visualization |
| **Google Colab** | Cloud-based development environment |

The presentation specifically reports Pandas, Matplotlib, NumPy and Seaborn as the essential libraries used.

---

## ☁️ Development Environment — Google Colab

Google Colab was used as the development environment because it:

- Removes the need for local software installation.
- Supports collaborative development.
- Provides access to the required Python data-analysis libraries.
- Makes the analysis accessible across different devices.

---

# 🧹 Data Preprocessing

The dataset used for the analysis is:

```text
Global Youtube Statistics.csv
