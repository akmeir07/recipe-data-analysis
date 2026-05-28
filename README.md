# FoodLens: Recipe Analytics & Machine Learning

## Overview
> **"What drives people to like and save recipes online?"**

The answer turned out to involve comfort food psychology, cultural identity, ingredient complexity, and the neuroscience of recipe titles.
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




## 📂 Project Structure

```
recipe-analysis/
│
├── data/
│   └── recipes_clean.csv        # Cleaned dataset (10,000+ recipes, 15 features)
│
├── notebooks/
│   └── recipe_analysis.ipynb    # Main Google Colab notebook
│
├── presentation/
│   └── recipe_website_analysis.pdf
│
└── README.md
```

---


## Pipeline

```
Web Scraping  →  Preprocessing  →  EDA  →  Hypothesis Testing  →  ML Models  →  Semantic Search
```

### 1 Data Collection — Web Scraping
**Source:** [eda.rambler.ru](https://eda.rambler.ru) · **Libraries:** `requests`, `BeautifulSoup`

The data wasn't available in plain HTML — it was embedded as **JSON inside the page source**. The scraping pipeline:

1. Extracted recipe card links from the main page
2. Visited each recipe page individually
3. Located and parsed the embedded JSON to extract structured fields

**Result:** 10,000+ rows × 15 columns, zero null values.

| Feature Category | Columns |
|---|---|
| Nutritional values | calories, proteins, fats, carbohydrates |
| Recipe characteristics | cuisine, dish type, ingredients, portion size, dietary category |
| User feedback | likes, dislikes |

### 2 Preprocessing

**Step 1 — Loading & Inspection**
Examined structure, dimensions, and data types. Removed duplicate records.

**Step 2 — Missing Values**
- `Cuisine` nulls → filled with `"Unknown"`
- Missing descriptions → filled from the `text` column

**Step 3 — Cleaning & Transformation**
- Standardized column names
- Fixed data types (numeric / categorical conversions)
- Transformed `Ingredients` from raw text into structured Python lists

**Step 4 — Outlier Handling**
- Identified outliers in `calories`, `fats`, `proteins`, `duration` via visualization
- Normalized total nutritional values by portion count → more realistic per-portion data

**Step 5 — Feature Engineering**

| New Feature | Description |
|---|---|
| `Likes Ratio` | Measures user satisfaction (likes / total votes) |
| `Calories per Portion` | More accurate nutritional metric |
| `Dietary Focus` | Categorizes recipes: High Protein, Balanced, High Carbs, etc. |
| `Dish Type` | Extracted from URL: breakfast, dessert, salad, etc. |
| `Time Effort` | Grouped cooking time into Express / Standard / Time-Consuming |

Ingredients were also exploded into a separate structure using `df.explode()` for per-ingredient analysis.

**Step 6 — Encoding & Standardization**
- Categorical variables (e.g. `Cuisine`) encoded to numerical format for ML
- Numerical features scaled for consistent model performance

---

##  Key Findings

###  Carbs Win. Always.
High-calorie recipes get **27% more likes** on average (p = 0.003). But the surprise: it's not fat — it's **carbs** that drive engagement. Comfort foods (bread, pasta, potatoes) beat "heavy/greasy" foods every time.

> *"The heart wants indulgence, but the click follows comfort and culture."*

###  Culture Matters
Italian vs. Russian cuisine t-test (p = 0.014): **Italian recipes get 36% more likes**.  
Italian food leverages universally loved ingredients (pasta, cheese, tomato). Russian cuisine is "niche gourmet" — high barrier to entry for the average global user.

**For content creators:** Post Italian for consistent growth. Post Russian for niche authority.

###  The Quick & Healthy Paradox
Low-calorie and high-protein meals are **actually faster to prepare** than high-carb/fat dishes. The myth that healthy eating takes too much time is debunked by the data.

###  The 8-Ingredient Sweet Spot
The optimal number of ingredients for maximum saves is **8**. Complexity scares people away. Correlation between ingredient count and saves: **-0.13**.

Exception: recipes with 35+ ingredients (elaborate wedding/event dishes) see an unexpected spike — the "Special Occasion" effect.

###  Simplicity Wins — Even in Titles
Short recipe names drive virality. Our brains prefer **"Brownies"** over **"Artisanal Hand-Crafted Cocoa Squares."** Complexity in the title creates a measurable barrier to engagement.

###  Risk vs. Reward: Polarizing Dishes
Breakfasts and drinks are the most "controversial" dish types (highest dislikes per like). Likely reason: high expectations for "simple" categories lead to disappointment.

---

## Machine Learning

### Model 1 — Calorie Predictor
> *"Can we guess the calories if we only know the macros?"*

| Metric | Value |
|--------|-------|
| R² Score | **0.96** |
| Top Predictor | Fat (69% importance) |
| Use Case | Instant calorie calculator for untagged recipes |

### Model 2 — Semantic Recipe Search
Built using **SentenceTransformer** to understand search *intent*, not just keywords.

| Query (RU) | Top Score | Result |
|------------|-----------|--------|
| ПП завтрак с яйцами | 0.82 |  Excellent |
| быстрый ужин с курицей | 0.81 | Perfect |
| завтрак для детей | 0.72 |  Strong |

**Lesson learned:** AI is only as good as the diversity of the training data — the model revealed a data gap weighted toward drinks/bar menus.

---

##  Recommendations

**For Content Creators & Chefs:**
- Use the **8-ingredient rule** — simplicity converts
- **Rebrand healthy options** to mimic comfort-food aesthetics
- Keep **recipe titles short** — every extra word loses engagement

**For Platform Developers (eda.rambler.ru):**
- Implement **automated calorie tagging** using the ML model
- Add **dynamic search filtering** (by time, dietary focus)
- Build **personalization** based on cuisine affinity

---

##  Visualizations

The notebook includes:
- Distribution of avg. carbs & fats by cuisine
- Average vs. Maximum likes by dietary focus (`High Carbs`, `Balanced`, `High Fat`, etc.)
- Which cuisines drive the "High Fat" category (European, French, Russian stand out)
- Heatmap: Preparation speed × Nutritional focus
- Scatter plot: Title length vs. saves
- Saves vs. number of ingredients (with confidence bands)
- Ingredient Impact: Popularity drivers vs. engagement killers
- Calorie prediction: actual vs. predicted scatter plot

---

# Author

Akmeiir Amirseit

Statistics and Data Science Student



