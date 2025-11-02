# 🎬 IMDb Movie Data Analysis using SQL

## 🧭 Project Overview
This project focuses on **analyzing IMDb movie data** using **SQL** to uncover insights into the film industry — including top-rated movies, popular genres, director performance, and revenue trends.  
By leveraging structured queries, the project demonstrates how SQL can be used for **data exploration, performance evaluation**, and **trend analysis** in real-world datasets.

---

## 🗂️ Dataset
The dataset includes information about **movies**, **genres**, **directors**, **actors**, and **box office collections**.  
It is structured in multiple relational tables as follows:

| Table Name | Columns |
|-------------|----------|
| **movie** | id, title, year, date_published, duration, country, worldwide_gross_income, languages, production_company |
| **genre** | movie_id, genre |
| **director_mapping** | movie_id, director_id |
| **director** | id, name |
| **actor_mapping** | movie_id, actor_id |
| **actor** | id, name, birth_year |
| **ratings** | movie_id, average_rating, votes |

---

## 🎯 Objectives
- Identify the **highest-rated movies**  
- Find the **most popular genres** based on average ratings  
- Determine **top-performing directors**  
- Analyze the **relationship between budget and revenue**  
- Identify **trends in movie production over time**

---

## 🧮 SQL Queries

### 1️⃣ Top 10 Highest-Rated Movies
```sql
SELECT title, average_rating, votes 
FROM movie m 
JOIN ratings r ON m.id = r.movie_id 
ORDER BY average_rating DESC, votes DESC 
LIMIT 10;

### 2️⃣ **Most Popular Genres**
SELECT g.genre, AVG(r.average_rating) AS avg_rating 
FROM genre g 
JOIN ratings r ON g.movie_id = r.movie_id 
GROUP BY g.genre 
ORDER BY avg_rating DESC;

### 3️⃣ Top Directors by Average Movie Rating
SELECT d.name, AVG(r.average_rating) AS avg_director_rating 
FROM director d 
JOIN director_mapping dm ON d.id = dm.director_id 
JOIN movie m ON dm.movie_id = m.id 
JOIN ratings r ON m.id = r.movie_id 
GROUP BY d.name 
ORDER BY avg_director_rating DESC 
LIMIT 10;

### 4️⃣ Revenue Analysis
SELECT title, worldwide_gross_income 
FROM movie 
WHERE worldwide_gross_income IS NOT NULL 
ORDER BY worldwide_gross_income DESC;

### 5️⃣ Number of Movies Released Per Year
SELECT year, COUNT(*) AS movie_count 
FROM movie 
GROUP BY year 
ORDER BY year;


🧰 Tools Used


🗄️ Database: MySQL


💻 Query Execution: SQL Workbench / Jupyter Notebook with SQL extensions



📊 Results & Insights

🎥 Highly-rated movies often have a large number of audience votes, indicating strong engagement.
🎭 Drama and Thriller genres tend to perform consistently well in ratings.
🎬 Certain directors show high average ratings across multiple films, highlighting consistent quality.
💰 Revenue analysis reveals that blockbuster hits dominate top rankings.
📈 Movie production trends fluctuate across decades, with spikes during high-growth cinema eras.
🔮 Future Improvements
📅 Expand dataset to include more years and international films.
🌍 Integrate streaming performance and audience demographics data.
🤖 Apply machine learning models to predict box office success or rating trends.

🏁 Conclusion
This project demonstrates the power of SQL for data analytics — enabling detailed insights into the movie industry’s patterns, performance, and evolution.
It highlights how structured data queries can extract meaningful business and creative insights from complex datasets.

👨‍💻 Author
Anuj Shelly
📍 Berlin, Germany

