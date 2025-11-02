# 🎬 IMDb Movie Data Analysis using SQL

## 🧭 Project Overview
This project analyzes **IMDb movie data** using **SQL** to uncover insights into the film industry — such as **top-rated movies, popular genres, director performance, and revenue trends**.  
It demonstrates how SQL can be leveraged for **data exploration, pattern discovery, and performance evaluation** in real-world datasets.

---

## 🗂️ Dataset
The dataset includes information about **movies**, **genres**, **directors**, **actors**, and **box office collections**.  
It is organized into multiple relational tables:

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
- Determine the **most popular genres**  
- Analyze **top-performing directors**  
- Study the **relationship between revenue and ratings**  
- Track **movie production trends** over time  

---

## 🧮 SQL Queries

Below are the key SQL queries used for the analysis, covering different analytical objectives:

```sql
-- 1️⃣ Top 10 Highest-Rated Movies
SELECT title, average_rating, votes 
FROM movie m 
JOIN ratings r ON m.id = r.movie_id 
ORDER BY average_rating DESC, votes DESC 
LIMIT 10;

-- 2️⃣ Most Popular Genres by Average Rating
SELECT g.genre, AVG(r.average_rating) AS avg_rating 
FROM genre g 
JOIN ratings r ON g.movie_id = r.movie_id 
GROUP BY g.genre 
ORDER BY avg_rating DESC;

-- 3️⃣ Top Directors by Average Movie Rating
SELECT d.name, AVG(r.average_rating) AS avg_director_rating 
FROM director d 
JOIN director_mapping dm ON d.id = dm.director_id 
JOIN movie m ON dm.movie_id = m.id 
JOIN ratings r ON m.id = r.movie_id 
GROUP BY d.name 
ORDER BY avg_director_rating DESC 
LIMIT 10;

-- 4️⃣ Revenue Analysis - Highest Grossing Movies
SELECT title, worldwide_gross_income 
FROM movie 
WHERE worldwide_gross_income IS NOT NULL 
ORDER BY worldwide_gross_income DESC;

-- 5️⃣ Number of Movies Released Per Year
SELECT year, COUNT(*) AS movie_count 
FROM movie 
GROUP BY year 
ORDER BY year;


🧰 Tools Used
🗄️ Database: MySQL
💻 Query Execution: SQL Workbench / Jupyter Notebook (SQL extensions)
📊 Results & Insights
🎥 Top-rated movies often have high vote counts → strong audience engagement.
🎭 Drama and Thriller genres consistently rank among the most popular.
🎬 A few directors maintain excellent track records, indicating high-quality outputs.
💰 Revenue distribution shows blockbuster dominance with large financial gaps.
📈 Movie production trends vary significantly across decades, reflecting shifts in the global cinema landscape.
🔮 Future Improvements
🗓️ Expand dataset to include more years and international titles.
🌍 Integrate data from streaming platforms and audience demographics.
🤖 Apply machine learning for predicting movie success based on features like genre, budget, or cast.

🏁 Conclusion
This project showcases how SQL can transform raw relational data into meaningful insights.
Through careful querying, it provides a data-driven perspective on industry trends, creative performance, and audience preferences.

👨‍💻 Author
Anuj Shelly
📍 Berlin, Germany
📧 anuj.shelly@gmail.com
