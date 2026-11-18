# Google Play Store Apps - Exploratory Data Analysis (EDA)

**App Insights Unlocked: A Data Analytics Challenge**

This project is an exploratory data analysis of the Google Play Store apps dataset. I worked as a data analyst for a mobile app company that wants to know what makes an app successful, which categories are popular, and how app size and price are related to ratings, reviews and installs.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Problem Statement](#problem-statement)
3. [Dataset](#dataset)
4. [Repository Structure](#repository-structure)
5. [Requirements](#requirements)
6. [Tools and Technologies](#tools-and-technologies)
7. [Project Workflow](#project-workflow)
8. [Visualizations](#visualizations)
9. [Key Insights](#key-insights)
10. [Challenges Faced](#challenges-faced)
11. [Recommendations](#recommendations)
12. [How to Run This Project](#how-to-run-this-project)
13. [Author](#author)

---

## Project Overview

A tech company that builds mobile apps has bought the Google Play Store dataset. The company wants to use it to improve its app development strategy, give users a better experience, and increase downloads and revenue.

My job was to go through the data, clean it, find patterns, and give clear recommendations. The full analysis is in the Jupyter notebook, written step by step with a short insight after every result.

**Main questions this project answers**
- What are the key factors behind an app's success on the Play Store?
- How can the company use these factors to improve its own apps?
- What can we learn about user preferences and behaviour?

**Stakeholders:** app developers, product managers, the marketing team, senior management, app users, advertisers and partners.

---

## Problem Statement

The task is to find patterns and trends in the data that can guide the company's decisions. The analysis focuses on:
- what factors contribute to high app ratings
- which app categories are the most popular
- how app size and price affect reviews and installs

The complete case study (background, stakeholders, data dictionary and all questions) is in `Problem_Statement.docx`.

---

## Dataset

- **Source:** [Google Play Store Apps - Kaggle](https://www.kaggle.com/datasets/lava18/google-play-store-apps?select=googleplaystore.csv)
- **File used:** `googleplaystore.csv`
- **Size:** 10,841 rows and 13 columns (9,659 unique apps after cleaning)

| Column | Description |
|---|---|
| App | Name of the app |
| Category | Category of the app |
| Rating | Average user rating (0-5) |
| Reviews | Number of user reviews |
| Size | Size of the app |
| Installs | Number of installs (a range like 1,000+) |
| Type | Free or Paid |
| Price | Price of the app |
| Content Rating | Age group the app is suitable for |
| Genres | Genre of the app |
| Last Updated | Date the app was last updated |
| Current Ver | Current version of the app |
| Android Ver | Minimum Android version needed |

> The dataset file is not uploaded in this repository. Please download it from the Kaggle link above and keep `googleplaystore.csv` in the same folder as the notebook.

---

## Repository Structure

```
google-play-store-app-eda/
│
├── Google_Play_Store_EDA.ipynb                  # Complete analysis (cleaning, EDA, insights)
├── Problem_Statement.docx                       # Case study and all questions
├── requirements.txt                             # Python libraries needed
├── Free Vs Paid.png.png                         # Chart: free vs paid apps
├── Top 10 Categories Avg.Rating.png.png         # Chart: top 10 categories
├── .gitignore
└── README.md                                    # Project documentation
```

---

## Requirements

- Python 3.8 or higher
- Jupyter Notebook (or JupyterLab / VS Code with the Jupyter extension)
- The libraries listed in `requirements.txt`:
  - pandas
  - numpy
  - matplotlib

Install them with:

```bash
pip install -r requirements.txt
```

---

## Tools and Technologies

| Tool | Use |
|---|---|
| Python | Main programming language |
| Pandas | Data cleaning, grouping, filtering and calculations |
| NumPy | Numerical operations (log scale, NaN handling) |
| Matplotlib | Bar charts, histograms, pie chart, scatter plots and box plot |
| Jupyter Notebook | Writing code and explanations together |
| Git and GitHub | Version control and sharing the project |

---

## Project Workflow

**1. Understanding the data**
Looked at the first and last rows, shape, columns, data types and summary statistics.

**2. Data cleaning**
- Removed 483 fully duplicate rows
- Removed 1 wrong row where the values were shifted by one column
- Converted `Reviews`, `Installs`, `Price` and `Size` from text to numbers, and `Last Updated` to a date
- Kept only one row for every app name (the one with the most reviews)
- Handled missing values (see the challenges section)
- Cleaned the `Category` text and created `Main_Genre` and `Updated_Year` columns

**3. Analysis**
Answered 10 basic, 10 medium and 4 advanced questions, each with a chart or table and a short written insight. Topics include average rating, categories, size distribution, free vs paid, content rating, top installed apps, correlations, price vs rating, genres, update frequency, binned installs vs rating and genre vs rating.

**4. Findings and recommendations**
Summarized the key findings and gave recommendations for the company's app strategy.

---

## Visualizations

### Free vs Paid Apps

![Free vs Paid Apps](Free%20Vs%20Paid.png.png)

Only 7.8% of apps on the Play Store are paid. Free apps make up 92.2% of the market.

### Top 10 Categories by Average App Size

![Top 10 Categories by Average App Size](Top%2010%20Categories%20Avg.Rating.png.png)

Game apps are the biggest by a clear margin (about 41.7 MB on average), followed by Family and Travel And Local apps.

---

## Key Insights

**Ratings**
- The average rating is **4.17** (median 4.3). **76.7%** of rated apps are rated 4.0 or above, so 4.0 is only the normal level in this store.
- **Events** (4.44), Art And Design (4.36) and Education (4.35) are the highest rated categories. **Dating** (3.98) is the lowest, but the gap between categories is small.
- Apps with 1K-100K installs have the lowest average rating (about 4.04). Ratings improve as apps grow and reach 4.37 for apps with 100M+ installs.

**Categories and installs**
- **Family** has the most apps (1,876), followed by Game (946) and Tools (829).
- **Game** has by far the most installs (about 13.5 billion), followed by Communication and Tools.
- Among genres, Tools has the most apps with 1M+ installs (275).

**Free vs paid**
- **92.2%** of apps are free and only 7.8% are paid.
- Free apps get far more reviews: about 234,421 on average compared to 8,748 for paid apps (median 1,379 vs 88).
- Apps priced above $10 have a lower average rating (4.13) than cheaper apps (about 4.3).

**What does not guarantee success**
- Rating and installs are almost unrelated (correlation 0.04). Price and rating (-0.11) and size and installs (0.13) are also weak. No single factor guarantees installs.

**Size and updates**
- Most apps are small - the median size is 12 MB. Games are the biggest on average.
- 65% of the apps were last updated in 2018. About 30% were updated in the last month of the data, but 25% have not been updated for over a year.
- The most reviewed apps (Facebook, WhatsApp, Instagram) also have 100M+ installs and keep ratings between 4.0 and 4.7.

---

## Challenges Faced

1. **A wrongly shifted row:** One record had all its values moved by one column and its category showed as `1.9`. It is not a real app record, so I removed it.
2. **Data stored as text:** `Reviews`, `Installs` (like `10,000+`), `Price` (like `$4.99`) and `Size` (like `19M`, `201k`) were all text. I had to remove the symbols and convert them to numbers, and convert `k` into MB.
3. **Duplicate and repeated apps:** Besides 483 exact duplicate rows, many apps appeared more than once with different review counts. I kept the row with the most reviews for each app.
4. **Missing values:** About 1,463 apps have no rating and 1,228 apps have the size "Varies with device". I did not fill them with the mean or median, because that would make the data look more average than it is. I let them stay empty and ignored them in calculations.
5. **Installs are ranges, not exact numbers:** Since values like `1,000,000,000+` are bands, 20 apps tie for the top. I used the number of reviews to break the tie for the top 5 most installed apps.
6. **Update frequency:** After removing duplicates, each app has only one update date, so the gap between updates of the same app cannot be calculated. I measured the number of days since each app was last updated instead.
7. **Sentiment analysis not possible:** This dataset has the number of reviews but not the review text, so the sentiment analysis question could not be done.
8. **Skewed data:** A few very popular apps (billions of installs and millions of reviews) pull the averages up, so I also checked medians and used a log scale in some charts.

---

## Recommendations

**For the company's app strategy**
1. **Aim for a rating above 4.3**, not just 4.0, because 4.0 is already normal in this store.
2. **Choose the category carefully.** Game, Communication and Tools bring the most installs, while categories like Events, Education and Art And Design have fewer apps and are very well rated.
3. **Use a free (freemium) model.** Free apps reach more users and collect many more reviews. If an app is paid, keep the price low (under $5), because the most expensive apps are rated slightly lower.
4. **Keep the app size reasonable.** Size has only a weak link with installs, so there is no need to remove useful features, but big apps like games should justify the download size.
5. **Update the app regularly** so it stays in the active group and does not go a year without an update.
6. **Encourage users to leave reviews.** The most installed apps also have the most reviews, and reviews build trust for new users.

**For improving this project further**
- Add the user reviews dataset to do sentiment analysis and find common complaints and praise.
- Add a machine learning model to predict an app's rating or installs.
- Build an interactive dashboard (Power BI, Tableau or Streamlit) from these results.
- Use a dataset with several update dates per app to measure the real update frequency.

---

## How to Run This Project

1. Clone the repository
   ```bash
   git clone https://github.com/ShubhamShah1/google-play-store-app-eda.git
   cd google-play-store-app-eda
   ```
2. Install the libraries
   ```bash
   pip install -r requirements.txt
   ```
3. Download `googleplaystore.csv` from [Kaggle](https://www.kaggle.com/datasets/lava18/google-play-store-apps?select=googleplaystore.csv) and place it in the same folder as the notebook.
4. Open the notebook
   ```bash
   jupyter notebook Google_Play_Store_EDA.ipynb
   ```
5. Run all the cells (Kernel > Restart & Run All).

---

## Author

**Shubham Shah**  
GitHub: [ShubhamShah1](https://github.com/ShubhamShah1)

If you liked this project, please give it a star.
