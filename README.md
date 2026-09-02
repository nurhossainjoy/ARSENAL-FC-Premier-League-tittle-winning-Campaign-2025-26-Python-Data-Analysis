# ⚽ Arsenal FC – Premier League Player Performance Analysis

## 📌 Project Overview

This project is solely made to showcase the author's love, admiration and emotion towards the EPL Club ARSENAL FC. The club won the Premier league after 22 years and the author is not gonna hold himself back from demonstrating how much he loves the club. This project is a simple metaphor of love toward the club. "North London Forever. Whatever the weather."
This project presents an exploratory data analysis (EDA) of Arsenal FC's Premier League player and match performance data using **Python, Pandas, NumPy, Matplotlib, and Seaborn**.

The project focuses on analyzing player performance, attacking and defensive contributions, shooting efficiency, discipline, match-week performance, home vs away performance, attendance, and other statistical aspects of Arsenal's Premier League campaign.

The analysis is performed using a dataset containing **585 records and 39 columns**, covering player-level and match-level statistics.

---

## 🎯 Project Objectives

The main objectives of this project are to:

- Explore and understand the Arsenal FC dataset
- Check data quality and identify potential issues
- Analyze top goal scorers and assist providers
- Evaluate player goal contributions
- Identify the most-used players
- Analyze shooting performance and shooting accuracy
- Calculate goals per 90 minutes
- Evaluate defensive contributions
- Analyze player discipline
- Compare performance across different positions
- Analyze performance by match week
- Compare player performance in home and away matches
- Analyze match attendance
- Create a custom player performance score
- Identify potentially underrated players
- Explore correlations between numerical variables
- Build a statistical Arsenal Dream XI
## 🐍 Python Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 📁 Dataset Information

The dataset contains Premier League match-by-match performance statistics of Arsenal FC players.

### Dataset Details

- **Total Records:** 585
- **Total Columns:** 39
- **File Name:** `Arsenal.csv`
- **Format:** CSV
- **Analysis Tool:** Python / Pandas

### 📌 Important Columns

| Column | Description |
|---|---|
| `Player` | Name of the Arsenal player |
| `Position` | Player's playing position |
| `Goals` | Goals scored |
| `Assists` | Assists provided |
| `Shots` | Total shots attempted |
| `Shots_On_Target` | Shots that were on target |
| `Tackles_Won` | Successful tackles |
| `Interceptions` | Number of interceptions |
| `Yellow_Cards` | Yellow cards received |
| `Red_Cards` | Red cards received |
| `Fouls_Committed` | Fouls committed |
| `Minutes` | Minutes played |
| `Match_Week` | Premier League match week |
| `Home_Team` | Home team |
| `Away_Team` | Away team |
| `Venue` | Match venue |
| `Attendance` | Match attendance |

---

## 🔍 Data Loading

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

data = pd.read_csv("Arsenal.csv")
```

---

## 📊 Dataset Overview

The first step of the analysis is to understand the structure of the dataset.

```python
data.shape
```

```python
data.columns
```

```python
data.info()
```

---

## 🧹 Data Quality Check

Missing values and duplicate records were checked to ensure the dataset was suitable for analysis.

```python
data.isnull().sum()
```

```python
data.duplicated().sum()
```

---

## ⚽ Player Performance Analysis

This project analyzes Arsenal players based on their attacking, defensive, shooting, discipline, and playing-time statistics.

### 1. Top Goal Scorers

Identify the top Arsenal players based on total goals scored.

```python
top_goal_scorers = (
    data.groupby("Player")["Goals"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

top_goal_scorers
```

---

### 2. Top Assist Providers

Identify the players with the highest number of assists.

```python
top_assist_providers = (
    data.groupby("Player")["Assists"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

top_assist_providers
```

---

### 3. Player Position Analysis

Analyze the different positions represented in the dataset.

```python
player_positions = data[["Player", "Position"]].drop_duplicates()

player_positions
```

---

### 4. Goal Contribution

Goal Contribution is calculated as:

> **Goal Contribution = Goals + Assists**

```python
data["Goal Contribution"] = data["Goals"] + data["Assists"]

top_goal_contributors = (
    data.groupby("Player")["Goal Contribution"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

top_goal_contributors
```

---

### 5. Most Used Players

Identify the players with the highest total playing minutes.

```python
most_used_players = (
    data.groupby("Player")["Minutes"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

most_used_players
```

---

### 6. Shooting Performance Analysis

Analyze total shots, shots on target, and goals for each player.

```python
shooting_performance = (
    data.groupby("Player")[["Goals", "Shots_On_Target", "Shots"]]
    .sum()
    .sort_values(by="Goals", ascending=False)
)

shooting_performance.head(10)
```

---

### 7. Shooting Accuracy

Shooting Accuracy is calculated using:

> **Shooting Accuracy = (Shots on Target / Shots) × 100**

```python
data["Shooting_Accuracy"] = np.where(
    data["Shots"] > 0,
    data["Shots_On_Target"] / data["Shots"] * 100,
    np.nan
)

data[["Player", "Shooting_Accuracy"]].head()
```

---

### 8. Goals per 90 Minutes

Goals per 90 minutes measures scoring efficiency based on playing time.

> **Goals per 90 = (Goals / Minutes) × 90**

```python
player_goals_minutes = (
    data.groupby("Player")[["Goals", "Minutes"]]
    .sum()
)

player_goals_minutes["Goals_Per_90"] = (
    player_goals_minutes["Goals"]
    / player_goals_minutes["Minutes"]
    * 90
)

player_goals_minutes.sort_values(
    by="Goals_Per_90",
    ascending=False
).head(10)
```

---

### 9. Defensive Performance

Defensive Contribution is calculated as:

> **Defensive Contribution = Tackles Won + Interceptions**

```python
data["Defensive_Contribution"] = (
    data["Tackles_Won"] + data["Interceptions"]
)

top_defensive_players = (
    data.groupby("Player")["Defensive_Contribution"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

top_defensive_players
```

---

### 10. Discipline Analysis

Analyze yellow cards, red cards, and fouls committed by Arsenal players.

```python
player_discipline = (
    data.groupby("Player")[
        ["Yellow_Cards", "Red_Cards", "Fouls_Committed"]
    ]
    .sum()
    .sort_values(
        by="Yellow_Cards",
        ascending=False
    )
)

player_discipline.head(10)
```

---

### 11. Position-wise Performance

Analyze player performance according to their positions.

```python
position_performance = (
    data.groupby("Position")[
        [
            "Goals",
            "Assists",
            "Shots",
            "Tackles_Won",
            "Interceptions",
            "Minutes"
        ]
    ]
    .mean()
)

position_performance
```

---

### 12. Match Week Performance

Analyze Arsenal's performance across different match weeks.

```python
match_week_performance = (
    data.groupby("Match_Week")[
        ["Goals", "Assists", "Shots"]
    ]
    .sum()
)

match_week_performance["Total_Performance"] = (
    match_week_performance["Goals"]
    + match_week_performance["Assists"]
    + match_week_performance["Shots"]
)

match_week_performance = (
    match_week_performance
    .sort_values(
        by="Total_Performance",
        ascending=False
    )
)

match_week_performance
```

---

### 13. Home vs Away Performance

Classify matches as Home or Away and compare player performance.

```python
data["Match_Type"] = data.apply(
    lambda row: "Home"
    if "Arsenal" in str(row["Home_Team"])
    else "Away",
    axis=1
)
```

```python
player_home_away = (
    data.groupby(
        ["Player", "Match_Type"]
    )[
        ["Goals", "Assists", "Shots", "Minutes"]
    ]
    .sum()
    .reset_index()
)

player_home_away
```

---

### 14. Attendance Analysis

Analyze match attendance and identify venues with the highest average attendance.

```python
max_attendance = data["Attendance"].max()
min_attendance = data["Attendance"].min()
average_attendance = data["Attendance"].mean()

print("Maximum Attendance:", max_attendance)
print("Minimum Attendance:", min_attendance)
print("Average Attendance:", average_attendance)
```

```python
venue_attendance = (
    data.groupby("Venue")["Attendance"]
    .mean()
    .sort_values(ascending=False)
)

venue_attendance
```

---

## 🏆 Custom Performance Score

A custom Performance Score was created to evaluate players using multiple statistical categories.

### Formula

> **Performance Score = (Goals × 5) + (Assists × 3) + Shots on Target + Tackles Won + Interceptions**

```python
player_performance = (
    data.groupby("Player")[
        [
            "Goals",
            "Assists",
            "Shots_On_Target",
            "Tackles_Won",
            "Interceptions"
        ]
    ]
    .sum()
)

player_performance["Performance_Score"] = (
    player_performance["Goals"] * 5
    + player_performance["Assists"] * 3
    + player_performance["Shots_On_Target"]
    + player_performance["Tackles_Won"]
    + player_performance["Interceptions"]
)

player_performance = (
    player_performance
    .sort_values(
        by="Performance_Score",
        ascending=False
    )
)

player_performance
```

---

## 💎 Underrated Player Analysis

Players with relatively lower playing minutes but strong goal contributions per 90 minutes were analyzed.

```python
underrated_analysis = (
    data.groupby("Player")[
        ["Goals", "Assists", "Minutes"]
    ]
    .sum()
)

underrated_analysis["Goal_Contribution"] = (
    underrated_analysis["Goals"]
    + underrated_analysis["Assists"]
)

underrated_analysis["Goal_Contribution_per_90"] = (
    underrated_analysis["Goal_Contribution"]
    / underrated_analysis["Minutes"]
    * 90
)

underrated_players = (
    underrated_analysis[
        (underrated_analysis["Minutes"] < 1000)
        & (underrated_analysis["Minutes"] >= 500)
    ]
    .sort_values(
        by="Goal_Contribution_per_90",
        ascending=False
    )
)

underrated_players
```

---

## 📈 Correlation Analysis

Correlation analysis is used to understand relationships between numerical variables in the dataset.

```python
numeric_data = data.select_dtypes(
    include=["int64", "float64"]
)

correlation = numeric_data.corr()
```

### Correlation Heatmap

```python
plt.figure(figsize=(14, 10))

sns.heatmap(
    correlation,
    annot=True,
    cmap="coolwarm",
    fmt=".2f"
)

plt.title("Correlation Heatmap")
plt.show()
```

---

# 🏟️ Arsenal Statistical Dream XI

A statistical Dream XI can be created by considering player performance across different positions.

### Formation

**4-3-3**

```text
                    Goalkeeper

Right Back     Center Back     Center Back     Left Back

             Central Midfielder
        Central Midfielder    Attacking Midfielder

       Right Wing     Striker     Left Wing
```

The Dream XI selection considers:

- Goals
- Assists
- Goal Contribution
- Minutes Played
- Shooting Performance
- Defensive Contribution
- Performance Score
- Player Position

---

# 📊 Key Findings

Based on the analysis, several important observations were identified:

- Viktor Gyökeres was one of the strongest attacking performers.
- Bukayo Saka contributed significantly through both goals and assists.
- Leandro Trossard showed strong attacking contribution.
- Declan Rice and Martín Zubimendi provided significant overall contributions.
- Several defenders demonstrated strong defensive contributions through tackles and interceptions.
- Playing minutes helped identify the most regularly used players.
- Shooting statistics provided insights into attacking efficiency.
- Home and Away analysis allowed comparison of player performance in different match conditions.
- Attendance analysis provided insights into stadium and match attendance patterns.
- The custom Performance Score helped compare players using multiple statistical categories.

---

# 🛠️ Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook**
- **GitHub**

---

# 📂 Project Structure

```text
Arsenal-FC-Player-Performance-Analysis/
│
├── Arsenal.csv
│
├── Arsenal.ipynb
│
├── README.md
│
└── images/
    └── analysis-results.png
```

---

# 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### 2. Navigate to the Project Folder

```bash
cd Arsenal-FC-Player-Performance-Analysis
```

### 3. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Open Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the Notebook

Open:

```text
Arsenal.ipynb
```

Then run the cells sequentially.

---

# 🧠 Skills Demonstrated

Through this project, the following practical skills were developed:

- Data Loading
- Data Cleaning
- Data Exploration
- Data Aggregation
- GroupBy Operations
- Sorting and Filtering
- Feature Engineering
- Statistical Analysis
- Performance Metrics
- Correlation Analysis
- Data Visualization
- Pandas Data Manipulation
- NumPy Operations
- Matplotlib Visualization
- Seaborn Visualization
- Analytical Thinking

---

# 📚 Learning Outcomes

This project helped develop practical experience in:

- Working with real-world sports data.
- Understanding structured datasets.
- Performing exploratory data analysis.
- Creating custom analytical metrics.
- Comparing player performance.
- Using Pandas for data aggregation.
- Using NumPy for numerical calculations.
- Creating statistical visualizations.
- Interpreting correlations.
- Turning raw data into meaningful insights.

---

# 🔮 Future Improvements

Possible improvements for this project include:

- Adding expected goals (**xG**).
- Adding expected assists (**xA**).
- Adding progressive passes.
- Adding key passes.
- Adding possession-based statistics.
- Building an interactive dashboard.
- Creating player comparison visualizations.
- Adding team-level analysis.
- Developing a more advanced player rating system.
- Creating a machine learning model for player performance prediction.

---

# ⭐ Conclusion

This project demonstrates how Python can be used to analyze football data and extract meaningful insights from raw match statistics.

By using **Pandas, NumPy, Matplotlib, and Seaborn**, the project covers different aspects of Arsenal FC player performance, including attacking contribution, shooting, defending, discipline, playing time, match performance, and statistical relationships.

The project also demonstrates practical skills in **data analysis, feature engineering, statistical analysis, and data visualization**.

---

# 👨‍💻 Author

**MD Nur Hossain Joy**

Aspiring Data Analyst | Python | SQL | Excel | Power BI | Tableau

---

# 📬 Connect With Me

- **GitHub:** [MD NUR HOSSAIN JOY](https://github.com/nurhossainjoy)
- **LinkedIn:** [MD NUR HOSSAIN JOY](https://www.linkedin.com/in/md-nur-hossain-joy-0b0bb9190/)

---

# ⭐ Support

If you find this project useful, please consider giving the repository a ⭐ on GitHub.

Thank you for visiting this project! ⚽📊
