# FoodLens: Recipe Analytics & Machine Learning

## Overview

FoodLens is a data science project focused on large-scale recipe analytics using web scraping, machine learning, and natural language processing (NLP).

The project analyzes more than 10,000 recipes collected from the public website `eda.ru` to explore:

* recipe popularity,
* nutrition trends,
* user engagement patterns,
* and semantic recipe similarity.

The project combines web scraping, exploratory data analysis (EDA), feature engineering, statistical analysis, machine learning, and NLP techniques to generate meaningful business and consumer insights.

---

# Business Problem

Modern recipe platforms contain thousands of recipes, making it difficult for users to efficiently discover recipes that match their interests, dietary preferences, and nutritional needs.

Traditional keyword-based search systems often fail to capture semantic meaning and user intent. Additionally, food platforms may struggle to understand which recipe characteristics influence user engagement and popularity.

This project aims to:

* analyze factors affecting recipe popularity,
* improve recipe discovery using semantic search,
* predict nutritional values using machine learning,
* and generate data-driven insights for food recommendation systems.

---

# Skills Demonstrated

* Web Scraping
* Data Cleaning & Preprocessing
* Exploratory Data Analysis (EDA)
* Feature Engineering
* Statistical Analysis
* Hypothesis Testing
* Machine Learning
* Natural Language Processing (NLP)
* Data Visualization
* Semantic Search Systems

---

# Technologies Used

| Technology           | Purpose                             |
| -------------------- | ----------------------------------- |
| Python               | Main programming language           |
| Pandas               | Data manipulation and preprocessing |
| NumPy                | Numerical computations              |
| BeautifulSoup        | Web scraping                        |
| Requests             | HTTP requests                       |
| Scikit-learn         | Machine learning models             |
| SentenceTransformers | NLP embeddings & semantic search    |
| Matplotlib,plotly    | Data visualization                  |
| Seaborn              | Statistical visualization           |
| SciPy                | Statistical analysis                |

---

# Dataset Information

* Source: `eda.ru`
* Size: 10,000+ recipes
* Features: 15 meaningful columns

The dataset includes:

* nutritional values,
* recipe categories,
* ingredients,
* cooking duration,
* portion size,
* and user engagement metrics (likes/dislikes).

No API was used during data collection.

---

# Methodology

## 1. Data Collection

Recipe data was collected using web scraping techniques with `Requests` and `BeautifulSoup`.

The required information was stored in JSON format inside the webpage source code. JSON objects were extracted and parsed into a structured dataset.

---

## 2. Data Preprocessing

The preprocessing stage included:

* duplicate removal,
* missing value handling,
* outlier detection,
* data normalization,
* ingredient parsing,
* and feature engineering.

Additional features created:

* Likes Ratio
* Calories per Portion
* Dietary Focus
* Time Effort Categories
* Dish Type Categories

---

## 3. Exploratory Data Analysis (EDA)

EDA was performed to analyze:

* nutritional distributions,
* user engagement behavior,
* cuisine popularity,
* ingredient frequency,
* and cooking duration patterns.

### Calories Distribution

![Calories Distribution](images/calories_distribution.png)

### Correlation Heatmap

![Correlation Heatmap](images/heatmap.png)

### Cuisine Distribution

![Cuisine Distribution](images/cuisine_distribution.png)

---

## 4. Statistical Analysis

Statistical methods used:

* correlation analysis,
* distribution analysis,
* and hypothesis testing.

The project investigated relationships between nutritional characteristics and user engagement metrics.

---

## 5. Machine Learning

A regression model was developed to predict calorie values using recipe-related features.

### Machine Learning Workflow

* Feature Selection
* Train-Test Split
* Model Training
* Performance Evaluation

### Results

* Achieved R² Score: **0.96**

### Feature Importance

![Feature Importance](images/feature_importance.png)

---

## 6. Semantic Search System

An NLP-based semantic recipe search system was implemented using SentenceTransformer embeddings.

Recipes were converted into vector embeddings, allowing semantic similarity comparisons between recipes instead of traditional keyword matching.

### Semantic Search Example

![Semantic Search](images/semantic_search.png)

---

# Key Insights

* High-calorie recipes tend to receive higher user engagement
* Nutritional composition influences recipe popularity
* Semantic embeddings improve recipe search relevance
* Machine learning models effectively predict calorie values

---

# Project Structure

```bash
recipe-analytics-ml/
│
├── data/
├── images/
├── notebooks/
├── README.md
├── requirements.txt
└── recipe_analysis.ipynb
```

---

# Future Improvements

* Deploy as a web application
* Build a recommendation engine
* Improve semantic search performance
* Create interactive dashboards

---

# Author

Akmeiir Amirseit

Statistics and Data Science Student


