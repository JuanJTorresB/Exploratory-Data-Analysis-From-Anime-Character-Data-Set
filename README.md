
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

```py

content.info()
content.describe(include="all")

```

Key observations:

- The dataset has **10 columns** and **37,580 entries**.
- Most columns are of type `object` (strings), except `mal_id` and `favorites`, which are integers.
- Some columns have **missing values**, especially:
  - `name_kanji` (≈26% missing)
  - `nicknames` (≈85% missing)
  - `about` (≈43% missing)
  - `image_webp_small_url` has only 1 missing value.

These missing values will be analyzed and handled in a later step.

```py

content.head()

```

### 📊 Sample Data Preview

| mal_id | url                                                     | name            | name_kanji       | nicknames                                  | favorites | about                                      | image_jpg_url (not representative) | image_webp_url (not representative) | image_webp_small_url (not representative) |
|--------|----------------------------------------------------------|------------------|------------------|---------------------------------------------|-----------|---------------------------------------------|----------------|----------------|-----------------------|
| 1      | https://myanimelist.net/character/1/Spike_Spiegel        | Spike Spiegel    | スパイク・スピーゲル | NaN                                         | 48133     | Birthdate: June 26, 2044 Height: 185 cm... | ...            | ...            | ...                   |
| 2      | https://myanimelist.net/character/2/Faye_Valentine       | Faye Valentine   | フェイ・バレンタイン | NaN                                         | 9474      | Birthday: August 14, 1994 One of the me... | ...            | ...            | ...                   |
| 3      | https://myanimelist.net/character/3/Jet_Black            | Jet Black        | ジェット・ブラック   | Running Rock, Black Dog                     | 2239      | Jet, known on his home satellite as the... | ...            | ...            | ...                   |
| 4      | https://myanimelist.net/character/4/Ein                  | Ein              | アイン               | NaN                                         | 2378      | Ein is a Pembroke Welsh Corgi brought ... | ...            | ...            | ...                   |
| 5      | https://myanimelist.net/character/5/Ichigo_Kurosaki      | Ichigo Kurosaki  | 黒崎 一護           | Ichi-nii, Shinigami Daiko (Substitute Soul...) | 35561     | Race: Human Birthday: July 15 (Cancer)... | ...            | ...            | ...                   |


- Null value analysis

| Column                | % Missing Values |
|-----------------------|------------------|
| `mal_id`              | 0.000%           |
| `url`                 | 0.000%           |
| `name`                | 0.000%           |
| `name_kanji`          | 25.93%           |
| `nicknames`           | 85.11%           |
| `favorites`           | 0.000%           |
| `about`               | 42.74%           |
| `image_jpg_url`       | 0.000%           |
| `image_webp_url`      | 0.000%           |
| `image_webp_small_url`| 0.003%           |

   -  Most of the characters registred do not have nicknames
   - All characters have their MyAnimeList page

- Basic statistics and initial impressions

    - Favorites - Basic Stats

```py

favorites = content['favorites']

print("Favorites - Basic Stats")
print(f"Min: {favorites.min()}")
print(f"Max: {favorites.max()}")
print(f"Mean: {favorites.mean():.2f}")
print(f"Median: {favorites.median()}")
print(f"Standard Deviation: {favorites.std():.2f}")
print(f"25th Percentile: {favorites.quantile(0.25)}")
print(f"75th Percentile: {favorites.quantile(0.75)}")

# How many characters have 0 favorites?
print(f"Characters with 0 favorites: {(favorites == 0).sum()} ({(favorites == 0).mean()*100:.2f}%)")

# Characters with >1000 favorites
print(f"Characters with >1000 favorites: {(favorites > 1000).sum()}")

```

Min: 0
Max: 144778
Mean: 75.31
Median: 0.0
Standard Deviation: 1688.47
25th Percentile: 0.0
75th Percentile: 2.0
Characters with 0 favorites: 22997 (61.19%)
Characters with >1000 favorites: 318

    - Boxplot showing the distribution of character favorites (limited to < 1000)

![Boxplot showing the distribution of character favorites (limited to < 1000)](images\Boxplot-showing-the-distribution-of-character-favorites.png)

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