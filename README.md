
markdown
Copiar
Editar
# Exploratory Data Analysis from Anime Character Data Set

This project focuses on performing exploratory data analysis (EDA) on a comprehensive dataset of anime and manga characters extracted from [MyAnimeList](https://myanimelist.net/). The dataset provides detailed information about over 200,000 unique characters as of **July 17, 2025**.

📂 **Dataset source:**  
🔗 [Kaggle - Anime Character Database (July 2025)](https://www.kaggle.com/datasets/sazzadsiddiquelikhon/anime-character-database-july-2025/data)

---

## 📌 Project Objectives

The main goals of this EDA project are:

- To explore character popularity metrics such as the number of "favorites".
- To analyze biographical and name-based trends in anime characters.
- To practice key Python data analysis skills: cleaning, visualizing, and interpreting real-world data.
- To investigate NLP techniques for identifying character archetypes based on text descriptions.

---

## 📦 Dataset Overview

The dataset includes the following fields:

| Column               | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `mal_id`             | Unique MyAnimeList character ID                                             |
| `url`                | Direct link to the character’s MAL page                                     |
| `name`               | Character’s common name (usually in Romaji)                                 |
| `name_kanji`         | Character’s name in Japanese Kanji/Kana                                     |
| `nicknames`          | Comma-separated list of character nicknames                                 |
| `favorites`          | Number of users who marked the character as a favorite                      |
| `about`              | Character biography or description                                          |
| `image_jpg_url`      | Standard resolution image URL (JPG format)                                  |
| `image_webp_url`     | Standard resolution image URL (WebP format)                                 |
| `image_webp_small_url` | Small resolution image URL (WebP format)                                 |

---

## 🛠️ Tools & Libraries

- Python 3.x
- Pandas
- NumPy
- Seaborn & Matplotlib
- Scikit-learn (for future ML tasks)
- NLTK / spaCy (for future NLP analysis)
- Jupyter Notebook

---

## 📊 Sections of the Analysis

### 1. Initial Data Exploration

- Overview of the data structure and types
- Null value analysis
- Basic statistics and initial impressions

### 2. Data Cleaning

- Handling missing values
- Removing duplicates
- Standardizing text fields

### 3. Statistical Analysis

- Distributions of key features
- Top characters by favorites
- Correlations between fields

### 4. Data Visualization

- Histograms and boxplots
- Popularity trends
- Character description insights

### 5. Natural Language Processing (NLP)

- Text cleaning and preprocessing
- TF-IDF vectorization of the `about` field
- Clustering or keyword extraction

### 6. Predictive Analysis (optional/future)

- Can we predict popularity from character descriptions?
- Regression or classification models

---

## 📁 Folder Structure

Exploratory-Data-Analysis-From-Anime-Character-Data-Set/
├── data/
│ └── anime_characters.csv
├── notebooks/
│ └── eda.ipynb
├── images/
│ └── [charts and visualizations]
├── README.md
└── requirements.txt

## 🚀 How to Use

1. Clone this repository:
```bash
git clone https://github.com/JuanJTorresB/Exploratory-Data-Analysis-From-Anime-Character-Data-Set.git
```
```bash
Install dependencies:

pip install -r requirements.txt


```

Run the Jupyter notebook inside the notebooks/ folder to follow the full analysis.

## 🤖 Future Work
Merge with anime or manga datasets for cross-entity analysis

Explore deeper archetype classification using NLP

Build interactive dashboards

## 📄 License
This dataset is shared under the Open Database License. Contents: © Original Authors.