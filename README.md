
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

|    |   mal_id | url                                                 | name            | name_kanji           | nicknames                                                             |   favorites | about                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | image_jpg_url                                               | image_webp_url                                               | image_webp_small_url                                          |
|---:|---------:|:----------------------------------------------------|:----------------|:---------------------|:----------------------------------------------------------------------|------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------|:-------------------------------------------------------------|:--------------------------------------------------------------|
|  0 |        1 | https://myanimelist.net/character/1/Spike_Spiegel   | Spike Spiegel   | スパイク・スピーゲル | nan                                                                   |       48133 | Birthdate: June 26, 2044 Height: 185 cm (6' 1") Weight: 70 kg (155 lbs) Blood type: O Planet of Origin: Mars  Spike Spiegel is a tall and lean 27-year-old bounty hunter born on Mars. The inspiration for Spike is found in martial artist Bruce Lee who uses the martial arts style of Jeet Kune Do as depicted in Session 8, "Waltz For Venus". He has fluffy, dark green hair (which is inspired by Yusaku Matsuda's) and reddish brown eyes, one of which is artificial and lighter than the other. He is usually dressed in a blue leisure suit, with a yellow shirt and Lupin III inspired boots. A flashback in Session 6 revealed it was his fully functioning right eye which was surgically replaced by the cybernetic one (although Spike himself may not have conscious recollection of the procedure since he claims to have lost his natural eye in an "accident"). One theory is that his natural eye may have been lost during the pre-series massacre in which he supposedly "died". The purpose of this cybernetic eye is never explicitly stated, though it apparently gives him exceptional hand-eye coordination - particularly with firearms (Spike's gun of choice is a Jericho 941, as seen throughout the series). In the first episode, when facing a bounty-head using Red Eye, Spike mocks him, calling his moves "too slow". At first, this seems like posturing on Spike's part, but even with his senses and reflexes accelerated to superhuman levels by the drug, the bounty cannot even touch Spike. A recurring device throughout the entire show is a closeup on Spike's fully-natural left eye before dissolving to a flashback of his life as part of the syndicate. As said by Spike himself in the last episode, his right eye "only sees the present" and his left eye "only sees the past." Spike often has a bent cigarette between his lips, sometimes despite rain or "No Smoking" signs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | https://cdn.myanimelist.net/images/characters/11/516853.jpg | https://cdn.myanimelist.net/images/characters/11/516853.webp | https://cdn.myanimelist.net/images/characters/11/516853t.webp |
|  1 |        2 | https://myanimelist.net/character/2/Faye_Valentine  | Faye Valentine  | フェイ・バレンタイン | nan                                                                   |        9474 | Birthday: August 14, 1994  One of the members of the bounty hunting crew in the anime series Cowboy Bebop. Often seen with a cigarette and in a revealing outfit complete with bright yellow hot pants and a matching, revealing top, black suspenders, white boots, and a long-sleeved red shirt worn normally through the sleeves, not to mention her signature headband, she is unusually attractive, sporting a bob of violet hair, green eyes, fair skin, and a voluptuous body. Although appearing to be no more than her 23 years alive suggests, Faye is actually upwards of 74-years-old, having been put into cryogenic freeze after a space shuttle accident. During the course of the series (set in 2071), Faye manages to cross paths with Spike and Jet twice before she finally makes herself at home aboard their ship the second time, much to the consternation and disapproval of the two men, both of whom have their own reservations about women in general. Faye herself is brash, egotistical, and quite lazy, despite taking plenty of time to pamper and care for her own appearance. Faye has also been placed under arrest several times in the series and spends much time in handcuffs on the ship. She, at times, expects the boys to take care of bounties for her, while she sits by idly to reap the benefits and eat all their food, another source of conflict.  Seemingly little more than a thorn in her partners’ sides, Faye is actually a well-rounded member of the team. She can handle herself exceptionally well for a woman of her slight appearance, displaying at least once in the series (in "Cowboy Funk") that she packs quite a mean punch. Adept at flying, Faye has stood her ground just as well as Spike has in an aerial dogfight in her ship Red Tail, at times even against Spike in an aerial dogfight. She also excels with guns, and is first seen in the series completely disabling a ship with a Heckler &amp; Koch MP5, though she is immediately apprehended afterward. In the movie, she is seen with the same gun, in addition to her normal companion: a Glock 30. Where Faye really shines, however, is with her mouth. She has an almost unstoppable attitude, and even her sometimes innocent smile can be seen as dangerous. Sarcastic and presumptuous, she rarely appears weak or in need of support. She brags and takes care of herself, never trusting others, cheating and lying her way from one day to the next.   Throughout the series, though she retains her sarcastic demeanor and unpleasant nature up until the very end, it is easy to see her grow as a character. She learns to value her comrades, coming back to the Bebop when she realizes that it is the only home that she has left, naming it as the “only place I could return to”. She grows to understand the disadvantages of being a loner, and that even though her "family" is somewhat dysfunctional it is still a place where she will always belong.                                                                                     | https://cdn.myanimelist.net/images/characters/15/264961.jpg | https://cdn.myanimelist.net/images/characters/15/264961.webp | https://cdn.myanimelist.net/images/characters/15/264961t.webp |
|  2 |        3 | https://myanimelist.net/character/3/Jet_Black       | Jet Black       | ジェット・ブラック   | Running Rock, Black Dog                                               |        2239 | Jet, known on his home satellite as the "Black Dog" for his tenacity, is a 36-year-old former cop from Ganymede (a Jovian satellite) and acts as Spike's foil during the series. Physically, Jet is very tall with a muscular build. He wears a beard with no mustache, and is completely bald save for the back of his head. Spike acts lazy and uninterested, whereas Jet is hard working and a jack-of-all-trades. Jet was once an investigator in the Inter Solar System Police (ISSP) for many years until he lost his arm in an investigation that went awry when his corrupt partner (and friend at the time) betrayed him. His arm was replaced with a cybernetic limb (later revealed to be by choice, as biological replacements were possible, he wanted the fake arm as a reminder of what happened), yet his loss of limb coupled with the general corruption of the police force prompted Jet to quit the ISSP in disgust and become a freelance bounty hunter. Jet also considers himself something of a renaissance man: he cultivates bonsai trees, cooks, enjoys jazz/blues music (he named his ship the Bebop, referring to a type of jazz), especially Charlie Parker, and even has interest in Goethe. As a character, Jet is the quintessential oyaji or "dad" even though he often wishes people would view him as a more brotherly figure (so as not to seem old).  Jet is skilled with handguns, typically carrying a pre-2004 Walther P99, as well as the use of the netgun. He is good with hand to hand combat as well. Unlike Spike, Jet tends to use more raw muscle than technique. He is also a great mechanic and pilot. Aside from the converted interplanetary fishing trawler vessel Bebop, Jet flies a smaller ship called Hammerhead. The Hammerhead appears to be a modified (Jet added larger engines and fuel tanks) salvage-craft that uses a mechanical arm equipped with a harpoon as its main weapon, which is somewhat analogous to his own mechanical arm. Both the Hammerhead and the Bebop are able to land on water, and have a fishing theme, most likely because Ganymede's surface is mostly covered with water (it is later revealed that the Bebop was originally a fishing ship that Jet "customized" with larger engines).  During the series, it is revealed that Jet once lived with a woman named Alisa, who left him because he was too controlling. Later they meet up again when Alisa's new boyfriend Rhint is wanted for murder. Jet then ends up in a situation somewhat similar to that of Vicious, where he must hunt down a woman who broke his heart, and her lover.                                                                                                                                                                                                                                                                                                                                                                                                                                                              | https://cdn.myanimelist.net/images/characters/11/253723.jpg | https://cdn.myanimelist.net/images/characters/11/253723.webp | https://cdn.myanimelist.net/images/characters/11/253723t.webp |
|  3 |        4 | https://myanimelist.net/character/4/Ein             | Ein             | アイン               | nan                                                                   |        2378 | Ein is a Pembroke Welsh Corgi brought aboard the Bebop by Spike after a failed attempt to capture a bounty. Ein is a "data dog": while the televised series only briefly hints on the fact that this means Ein's brain was somehow enhanced drastically, the manga shows Ed accessing data stored in Ein's brain via a virtual reality-type interface with which she has a conversation with a human proprietor. It is obvious that Ein is abnormally intelligent, as he is able to answer the telephone, drive a car (just the wheel), use the SSW, play shōgi, and generally do a number of other things that an average canine should not be able to do, but he never talks in a human language during the show. He does, however, speak in Session 18 "Speak Like A Child" after the credits Ein tells Spike "Next Episode: Wild Horses". He is able to "speak" to other species, as demonstrated in Session 17, "Mushroom Samba" (he spoke to a cow with a subtitled bark of "Thanks", to which the cow has a subtitled moo back of "No problem"). It is likely that Ed is the only crew member with any idea of Ein's capabilities, as the other crew members are quick to dismiss Ein, and never seem to acknowledge him as more than a pet. Ein initially takes a shine to Jet, but when Ed joins the crew, he comes around to her as well. Frequently the two trade roles, with Ein expressing very human sentiments via facial expression and Ed regressing to a feral state. He went with Ed after she left the crew, probably because of his attachment to her. His name is a pun on the Japanese word for "dog" (犬 inu) but is also German for "one". "Ein" may also be short for "Einstein", after Albert Einstein, because of the extraordinary intelligence he possesses.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | https://cdn.myanimelist.net/images/characters/5/30624.jpg   | https://cdn.myanimelist.net/images/characters/5/30624.webp   | https://cdn.myanimelist.net/images/characters/5/30624t.webp   |
|  4 |        5 | https://myanimelist.net/character/5/Ichigo_Kurosaki | Ichigo Kurosaki | 黒崎 一護            | Ichi-nii, Shinigami Daiko (Substitute Soul Reaper), Itsygo, Ryoka Boy |       35561 | Race: Human Birthday: July 15 (Cancer) Age: 15 (beginning); 17 (currently) Height: 174-&gt;181 cm Weight: 61-&gt;66 kg Known Relatives: Isshin Kurosaki (father), Masaki Kurosaki (mother, deceased), Yuzu Kurosaki (younger sister), Karin Kurosaki (younger sister),   Theme Song: "Number One" by Hazel Fernandes and Shiro Sagisu.  For the most part, Ichigo appears like a normal teenage boy, the one exception to that is his spiky, orange hair, a trait which he has been ridiculed about for years. He is a fairly tall, and lean-built person with peach skin and brown eyes. Since becoming a Shinigami, he has become noticeably more muscular, as noted by his sister Karin. When in his spiritual form, Ichigo wears standard Shinigami attire with the addition of a strap across his chest.  When he was young, Ichigo considered his mother to be the center of his world. Ichigo always smiled whenever he was with Masaki and he was regularly at her side, holding her hand.  As a teenager, Ichigo's personality is much more complex. Stubborn, short-tempered, occasionally confrontational, determined, outspoken, strong-willed and impulsive, he attempts to maintain a detached and "cool" image, despite claiming to not care about what other people think about him. He generally keeps his face set in a permanent scowl with his eyebrows drawn together. Ichigo carries the burden of the real world and the spirit world (Soul Society), a task quite difficult, especially for a teenager like Ichigo, who has his own worries and problems. Also, Ichigo is quite smart; he was ranked 23rd in his high school. He does this partly to prove to his teachers and classmates that just because he's unique, or somewhat punkish, that he can still succeed.  When Ichigo first becomes a Shinigami, his Zanpakutō is a standard-looking katana, but oversized with an equally-oversized brown sheathe hung by a strap over his right shoulder. It has a rectangular bronze hand guard with gently inward-curved edges, a stylized flame pattern on the long sides, and a simple decorative slit on the short ones. The handle is red with two light blue tassels on the end of the handle. The large size is due to the unfocused but immense amount of Ichigo's spiritual power, which he didn't know how to control. As a result, the sword itself was rather weak, since very little spiritual power was used to create it. Nevertheless, it was powerful enough to subdue a Gillian-class Menos and lesser Hollows, completely blocking a Cero from the former. It was even able to upturn the ground with a single strike. Because of its weak spiritual energy nature, Byakuya Kuchiki was able to easily cut off most of the blade during his first encounter with Ichigo and Kisuke Urahara subsequently slices it down to the hilt during their training, forcing Ichigo to learn the name of his Zanpakutō in order to release its true form. This sword is found to be a result of Rukia's deprived spiritual energy and not a result of his own power. | https://cdn.myanimelist.net/images/characters/3/512788.jpg  | https://cdn.myanimelist.net/images/characters/3/512788.webp  | https://cdn.myanimelist.net/images/characters/3/512788t.webp  |

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