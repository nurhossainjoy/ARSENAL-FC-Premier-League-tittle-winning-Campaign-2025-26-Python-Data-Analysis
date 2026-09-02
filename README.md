# ⚽ Arsenal FC Premier League – Player Performance Analysis


---

## 📌 Project Overview

This project is an exploratory data analysis (EDA) of **Arsenal FC's Premier League player and match performance data** using Python.

The main purpose of this project is to analyze player performance from different perspectives, including attacking performance, shooting efficiency, defensive contribution, discipline, playing time, match-week performance, home vs away performance, attendance, player performance scoring, and statistical player evaluation.

The complete analysis was performed using **Python and Pandas in Jupyter Notebook**.

The project contains multiple analytical questions, starting from basic dataset exploration and gradually moving toward more advanced performance analysis.

---

# 🎯 Project Objectives

The main objectives of this project are:

- Understand the structure of the Arsenal FC dataset
- Explore player and match statistics
- Perform data quality checks
- Identify the top goal scorers
- Identify the top assist providers
- Analyze player positions
- Calculate goal contribution
- Identify the most-used players
- Analyze shooting performance
- Calculate shooting accuracy
- Calculate goals per 90 minutes
- Analyze defensive contribution
- Analyze player discipline
- Analyze position-wise performance
- Analyze performance by match week
- Compare home and away performance
- Analyze match attendance
- Create a custom player performance score
- Identify potentially underrated players
- Perform correlation analysis
- Create a statistical Arsenal Dream XI

---

# 🛠️ Technologies Used

The following technologies and Python libraries were used in this project:

### Programming Language

- Python

### Libraries

- Pandas
- NumPy
- Matplotlib
- Seaborn

### Development Environment

- Jupyter Notebook

---

# 📚 Python Libraries

#📂 Dataset Information

The project uses an Arsenal FC Premier League player and match statistics dataset.

The dataset contains 585 records and 39 columns.

The dataset includes both player-level statistics and match-level information.

#📊 Dataset Features

Some of the important columns used in the analysis are:

Column	Description
Player	Name of the player
Position	Player's playing position
Minutes	Total minutes played
Goals	Goals scored
Assists	Assists provided
Shots	Total shots
Shots_On_Target	Shots on target
Tackles_Won	Successful tackles
Interceptions	Number of interceptions
Yellow_Cards	Yellow cards received
Red_Cards	Red cards received
Fouls_Committed	Fouls committed
Match_Week	Premier League match week
Home_Team	Home team
Away_Team	Away team
Venue	Match venue
Attendance	Match attendance

#🔎 Exploratory Data Analysis

The project follows a structured analytical approach.

The analysis starts with understanding the dataset and then moves toward player-level performance analysis.

#1️⃣ Dataset Overview
Question

Explore the Arsenal FC dataset and identify:

Total number of rows
Total number of columns
Column names
Data types
General dataset structure
Purpose

This step provides an initial understanding of the dataset before performing further analysis.

#2️⃣ Data Quality Check
Question

Check the dataset for:

Missing values
Duplicate records
Potential data quality issues
Purpose

Data quality checking is an important part of any data analysis project because incorrect or incomplete data can affect analytical results.

#3️⃣ Top Goal Scorers ⚽
Question

Identify the Top 5 Arsenal players based on their total number of goals.

Analysis

The data was grouped by player and total goals were calculated.

Formula
Total Goals = Sum of Goals
Result

The leading goal scorers identified in the analysis include:

Rank	Player	Goals
1	Viktor Gyökeres	14
2	Bukayo Saka	7
3	Eberechi Eze	7
4	Leandro Trossard	6
5	Martín Zubimendi	5
#4️⃣ Top Assist Providers 🎯
Question

Identify the Top 5 Arsenal players based on total assists.

Analysis

Players were grouped and their total assists were calculated.

Formula
Total Assists = Sum of Assists

The analysis highlights the players who contributed most directly to Arsenal's goal creation.

#5️⃣ Player Position Analysis
Question

Analyze the different player positions represented in the dataset.

The analysis was performed using the Position and Player columns.

Purpose

This helps understand the positional structure of the Arsenal squad and the number of players associated with each position.

#6️⃣ Goal Contribution Analysis ⚽🎯

A new metric called Goal Contribution was created.

Formula
Goal Contribution = Goals + Assists
Python
data["Goal Contribution"] = data["Goals"] + data["Assists"]

The players were then ranked according to their total goal contribution.

Result

Some of the highest goal contributors include:

Player	Goal Contribution
Viktor Gyökeres	15
Bukayo Saka	12
Leandro Trossard	12
Declan Rice	9
Eberechi Eze	9
#7️⃣ Most Used Players ⏱️
Question

Identify the players with the highest total number of minutes played.

Formula
Total Minutes = Sum of Minutes
Purpose

This analysis identifies the players who were most heavily involved in Arsenal's matches during the season.

The analysis includes both outfield players and goalkeepers where applicable.

#8️⃣ Shooting Performance Analysis 🎯
Question

Analyze player shooting performance using:

Goals
Shots
Shots on Target
Analysis

The data was grouped by player and the total values for the shooting statistics were calculated.

Example
Shooting_performance = (
    data.groupby("Player")[["Goals", "Shots_On_Target", "Shots"]]
    .sum()
    .sort_values(by="Goals", ascending=False)
)
Purpose

This analysis helps identify:

High-volume shooters
Accurate shooters
Efficient attackers
Players who contribute most to Arsenal's attacking threat
#9️⃣ Shooting Accuracy 🎯

A new metric called Shooting Accuracy was created.

Formula
Shooting Accuracy =
(Shots on Target / Total Shots) × 100
Python
data["shooting_accuracy"] = (
    data["Shots_On_Target"] / data["Shots"] * 100
)

Players were then ranked based on their shooting accuracy.

Special consideration was given to cases where the number of shots was zero to avoid invalid calculations.

Purpose

Shooting accuracy helps measure how frequently a player's shots are actually on target.

#🔟 Goals per 90 Minutes ⚽
Question

Calculate player scoring efficiency using goals per 90 minutes.

Formula
Goals per 90 Minutes =
(Goals / Minutes) × 90
Purpose

This metric allows players with different amounts of playing time to be compared more fairly.

For example, a player with fewer total goals but significantly fewer minutes may have a higher goals-per-90 rate.

#1️⃣1️⃣ Defensive Performance 🛡️

A new metric called Defensive Contribution was created.

Formula
Defensive Contribution =
Tackles Won + Interceptions
Python
data["Defensive_Contribution"] = (
    data["Tackles_Won"] + data["Interceptions"]
)

Players were then ranked according to their total defensive contribution.

Purpose

This analysis identifies players who contributed strongly to defensive actions.

#1️⃣2️⃣ Discipline Analysis 🟨🟥

Player discipline was analyzed using:

Yellow Cards
Red Cards
Fouls Committed
Python
player_discipline = (
    data.groupby("Player")
    [["Yellow_Cards", "Red_Cards", "Fouls_Committed"]]
    .sum()
)

Separate rankings were created for:

Players with the most yellow cards
Players with the most red cards
Players committing the most fouls
Purpose

This analysis helps understand player disciplinary patterns.

#1️⃣3️⃣ Position-wise Performance Analysis
Question

Analyze player performance according to their positions.

The analysis focuses on performance metrics such as:

Goals
Assists
Shots
Tackles Won
Interceptions
Minutes
Purpose

The objective is to understand how different positions contribute to different aspects of Arsenal's overall performance.

For example:

Forwards are generally more involved in goals and shots
Midfielders contribute to both attacking and defensive actions
Defenders contribute more strongly through tackles and interceptions
#1️⃣4️⃣ Match Week Performance 📅
Question

Analyze Arsenal's performance across different Premier League match weeks.

The analysis includes:

Goals
Assists
Shots

A custom metric called Total_Performance was also created.

Formula
Total Performance =
Goals + Assists + Shots
Python
match_week_performance = (
    data.groupby("Match_Week")[["Goals", "Assists", "Shots"]]
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
Highest-Ranked Match Weeks

According to the custom Total_Performance metric, some of the highest-performing match weeks include:

Match Week	Goals	Assists	Shots	Total Performance
30	2	2	25	29
19	4	3	22	29
2	5	4	18	27
27	4	2	20	26
18	1	1	24	26
12	4	4	17	25
Purpose

This analysis helps identify the match weeks in which Arsenal players collectively produced the strongest attacking output according to the project's custom metric.

#1️⃣5️⃣ Home vs Away Performance 🏠✈️
Question

Separate Arsenal's matches into:

Home Matches
Away Matches

Then compare player performance between the two match types.

The analysis includes:

Goals
Assists
Shots
Minutes
Match Classification

A new column called Match_Type was created.

data["Match_Type"] = data.apply(
    lambda row:
    "Home" if "Arsenal" in str(row["Home_Team"])
    else "Away",
    axis=1
)
Explanation

The logic checks whether Arsenal appears in the Home_Team column.

If Arsenal is the home team:

Home

Otherwise:

Away
Player-wise Analysis
player_home_away = (
    data.groupby(
        ["Player", "Match_Type"]
    )[["Goals", "Assists", "Shots", "Minutes"]]
    .sum()
    .reset_index()
)
Purpose

This analysis helps determine whether individual players performed differently in:

Home matches
Away matches
#1️⃣6️⃣ Attendance Analysis 👥
Question

Analyze match attendance data.

The analysis includes:

Maximum attendance
Minimum attendance
Average attendance
Venue with the highest average attendance
Purpose

Attendance analysis provides additional insight into match-level information and stadium audience patterns.

#1️⃣7️⃣ Player Performance Score 🏆

A custom Performance Score was developed to evaluate players using multiple statistical categories.

Formula
Performance Score =
(Goals × 5)
+ (Assists × 3)
+ Shots on Target
+ Tackles Won
+ Interceptions
Python
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
Top Performance Scores
Rank	Player	Performance Score
1	Martín Zubimendi	115
2	Declan Rice	114
3	Bukayo Saka	112
4	Viktor Gyökeres	101
5	Jurriën Timber	96
6	Leandro Trossard	87
7	Eberechi Eze	83
8	Gabriel Magalhães	76
9	Piero Hincapié	65
10	Mikel Merino	59
Important Note

This is a custom analytical score created specifically for this project.

It is not an official football rating system.

#1️⃣8️⃣ Underrated Player Analysis 🔍
Question

Identify players who:

Played relatively fewer minutes
Produced a relatively high goal contribution per 90 minutes
Goal Contribution per 90 Formula
Goal Contribution per 90 =
(Goals + Assists) / Minutes × 90
Python
player_performance = (
    data.groupby("Player")
    [["Goals", "Assists", "Minutes"]]
    .sum()
)

player_performance["Goal_Contribution"] = (
    player_performance["Goals"]
    + player_performance["Assists"]
)

player_performance["Goal_Contribution_per_90"] = (
    player_performance["Goal_Contribution"]
    / player_performance["Minutes"]
    * 90
)

Players were filtered using the following minutes range:

Minutes >= 500
Minutes < 1000

This helps avoid focusing on players with extremely small sample sizes.

Purpose

The analysis attempts to identify players whose contribution may be understated when looking only at total goals or assists.

#1️⃣9️⃣ Correlation Analysis 📈
Question

Create a correlation analysis using numerical variables and identify which variables are most strongly related to goals.

Purpose

Correlation analysis helps understand relationships between different performance variables.

Examples of variables analyzed include:

Goals
Assists
Shots
Shots on Target
Tackles Won
Interceptions
Minutes
Other numerical statistics
Visualization

A correlation heatmap was used to visually represent relationships between numerical variables.

A value closer to:

+1

indicates a strong positive relationship.

A value closer to:

-1

indicates a strong negative relationship.

A value around:

0

indicates a weak or negligible linear relationship.

#2️⃣0️⃣ Arsenal Statistical Dream XI 🏆
Question

Build a statistical Arsenal Dream XI using a:

4-3-3 Formation

The player selection is based on statistical performance rather than personal preference.

Selection Criteria

The analysis considers:

Goals
Assists
Goal Contribution
Defensive Contribution
Minutes
Player Position
Overall Performance Score
Formation
                 ST
           
       LW                  RW

            CM      CM
                 DM

       LB     CB     CB     RB

                 GK
Important Note

The Dream XI is a statistical selection based on the available dataset.

It should not be interpreted as an official Arsenal starting XI or a subjective football ranking.

📊 Key Findings

The analysis produced several interesting findings from the dataset.

⚽ Leading Goal Scorer

Viktor Gyökeres recorded the highest number of goals in the analyzed data with:

14 Goals
#🎯 Goal Contribution

Viktor Gyökeres also recorded the highest goal contribution:

15 Goal Contributions

based on:

Goals + Assists
🏹 Attacking Performance

Bukayo Saka, Eberechi Eze, Leandro Trossard, Viktor Gyökeres and other attacking players contributed significantly to Arsenal's attacking output.

#🛡️ Defensive Contribution

The custom defensive contribution metric:

Tackles Won + Interceptions

highlighted players such as:

Martín Zubimendi
Declan Rice
Jurriën Timber
Piero Hincapié
Gabriel Magalhães
#🏆 Performance Score

The custom performance score identified Martín Zubimendi as the highest-rated player according to the project's statistical scoring model.

His score was:

115

followed by:

Declan Rice – 114
Bukayo Saka – 112
Viktor Gyökeres – 101
Jurriën Timber – 96
📈 Match Week Insights

The match-week analysis identified several highly productive match weeks.

The highest Total_Performance values were:

Match Week 30 → 29
Match Week 19 → 29
Match Week 2  → 27
Match Week 27 → 26
Match Week 18 → 26
Match Week 12 → 25

The Total_Performance metric combines:

Goals + Assists + Shots
#🧮 Custom Metrics Created

Several custom analytical metrics were created throughout the project.

Goal Contribution
Goal Contribution = Goals + Assists
Shooting Accuracy
Shooting Accuracy =
(Shots on Target / Shots) × 100
Goals per 90
Goals per 90 =
(Goals / Minutes) × 90
Defensive Contribution
Defensive Contribution =
Tackles Won + Interceptions
Goal Contribution per 90
Goal Contribution per 90 =
(Goals + Assists) / Minutes × 90
Performance Score
Performance Score =
(Goals × 5)
+ (Assists × 3)
+ Shots on Target
+ Tackles Won
+ Interceptions
Match Week Total Performance
Total Performance =
Goals + Assists + Shots

#🧠 Skills Demonstrated

This project demonstrates practical knowledge of several important data analysis concepts.

🐍 Python
Variables
Data types
Conditional logic
Lambda functions
Functions
Basic calculations
Data manipulation
🐼 Pandas
read_csv()
DataFrame
groupby()
sum()
mean()
min()
max()
sort_values()
head()
drop_duplicates()
reset_index()
pivot()
apply()
select_dtypes()
Boolean filtering
Creating calculated columns
#🔢 NumPy

NumPy was used for numerical operations and handling calculations such as shooting accuracy.

#📊 Data Visualization

The project uses:

Matplotlib
Seaborn
Correlation heatmaps
Statistical visualizations
#📈 Data Analysis

The project demonstrates:

Exploratory Data Analysis
Data aggregation
Data filtering
Ranking
Comparative analysis
Statistical analysis
Feature creation
Correlation analysis
Performance evaluation
#📁 Project Structure
Arsenal-FC-Data-Analysis/
│
├── Arsenal.ipynb
│
├── Arsenal.csv
│
└── README.md
📓 Arsenal.ipynb

The Jupyter Notebook contains the complete analysis.

It includes:

Dataset exploration
Data cleaning/checking
Player analysis
Statistical calculations
Custom metrics
Performance rankings
Home vs away analysis
Match-week analysis
Correlation analysis
Player performance evaluation
📄 Arsenal.csv

The CSV file contains the raw Arsenal FC player and match statistics used throughout the project.

#📘 README.md

This file provides an overview of the project, methodology, analytical questions, findings, technologies and project structure.

🚀 How to Run the Project
Step 1: Clone the Repository
git clone YOUR_GITHUB_REPOSITORY_URL
Step 2: Navigate to the Project Directory
cd Arsenal-FC-Data-Analysis
Step 3: Install Required Libraries
pip install pandas numpy matplotlib seaborn jupyter
Step 4: Start Jupyter Notebook
jupyter notebook
Step 5: Open the Notebook

Open:

Arsenal.ipynb

Then run the notebook cells sequentially.

#🔄 Reproducibility

To reproduce the analysis:

Download or clone the repository.
Make sure Arsenal.csv is located in the correct project directory.
Install the required Python libraries.
Open Arsenal.ipynb.
Run the notebook cells from top to bottom.
⚠️ Analytical Notes & Limitations

This project is primarily an exploratory data analysis project.

Some of the metrics used in the project are custom metrics created for analytical purposes.

For example:

Performance Score

and

Total Performance

are not official football statistics.

Similarly, a high correlation does not necessarily mean that one variable causes another.

The results should therefore be interpreted within the context of the available dataset.

#🔮 Future Improvements

This project can be further developed by adding more advanced football analytics.

Potential improvements include:

Expected Goals (xG)
Expected Assists (xA)
Progressive Passes
Progressive Carries
Key Passes
Chances Created
Pass Completion Rate
Defensive Duels
Aerial Duels
Ball Recoveries
Player Percentile Rankings
Advanced player rating models
Machine Learning-based player evaluation
Interactive Power BI dashboard
Interactive Tableau dashboard
Comparison with other Premier League teams
Multi-season performance analysis
Automated player scouting system
Statistical player recommendation system
#💡 Possible Future Dashboard

The analysis can later be transformed into an interactive dashboard using:

Power BI
Tableau
Excel

A dashboard could include:

Player Overview
      ↓
Attacking Performance
      ↓
Defensive Performance
      ↓
Shooting Analysis
      ↓
Home vs Away
      ↓
Match Week Trends
      ↓
Player Comparison
      ↓
Dream XI
🎓 Learning Outcomes

Through this project, I developed practical experience in working with sports performance data and converting analytical questions into Python-based solutions.

The major learning outcomes include:

Understanding real-world datasets
Performing exploratory data analysis
Working with Pandas DataFrames
Filtering and grouping data
Aggregating player statistics
Creating calculated columns
Designing custom performance metrics
Comparing players
Ranking players
Analyzing attacking statistics
Analyzing defensive statistics
Analyzing player discipline
Comparing home and away performances
Working with match-week data
Performing correlation analysis
Creating statistical visualizations
Building a complete end-to-end data analysis project

#📌 Conclusion

This Arsenal FC Player Performance Analysis project demonstrates how Python and Pandas can be used to transform raw football statistics into meaningful analytical insights.

The project covers the complete analytical workflow:

Raw Dataset
     ↓
Data Understanding
     ↓
Data Quality Check
     ↓
Data Transformation
     ↓
Exploratory Data Analysis
     ↓
Custom Metrics
     ↓
Player Performance Analysis
     ↓
Comparative Analysis
     ↓
Correlation Analysis
     ↓
Statistical Insights

The analysis provides a structured view of Arsenal's player performance from multiple perspectives, including attacking contribution, defensive contribution, shooting efficiency, playing time, discipline, match-week performance and home/away performance.

#👨‍💻 Author
MD Nur Hossain Joy

Aspiring Data Analyst / Data Scientist

Technical Interests
Python
Pandas
NumPy
SQL
PostgreSQL
Excel
Power BI
Tableau
Data Visualization
Exploratory Data Analysis
Machine Learning
🌐 Connect With Me
GitHub: https://github.com/nurhossainjoy
LinkedIn: https://www.linkedin.com/in/md-nur-hossain-joy-0b0bb9190/
Email: nurhossainjoy4456@gmail.com
