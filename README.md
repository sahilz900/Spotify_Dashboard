# 🎵 Spotify 2023 Dashboard – Power BI  

## 📌 Overview  
This **Power BI dashboard** analyzes **Spotify streaming data** from 2023, providing insights into **top songs, streaming trends, and artist performance**. The dataset was cleaned and transformed using **Power Query**, and key metrics were derived using **DAX calculations**.  

## 🛠 Data Processing  
- **Power Query:** Cleaned and structured the dataset for analysis.  
- **DAX Measures:** Created custom calculations to analyze top songs, streaming trends, and comparisons.  

## 📊 Key Insights & Visualizations  
### 🔹 **Charts & Graphs:**  
1. **Total Streams Over Time** – Trends in song streams across different periods.  
2. **Top Songs & Artists** – Highest-streamed songs and their respective artists.  
3. **Streaming Trends by Released Year** – Impact of song release year on popularity.  
4. **Monthly Streaming Patterns** – Seasonal trends in streaming activity.  
5. **Top 10 Most Streamed Songs** – Songs with the highest play count.  
6. **Comparison of Top Song vs. Average Streams** – How the most streamed song compares to the average.  

### 🔹 **Slicers (Filters) Used:**  
- **Released Year**  
- **Artist Name**  
- **Month**  

### 🔹 **Key DAX Measures:**  
- **Total Released Year Sum** → `SUM('spotify-2023'[released_year])`  
- **Max Streams** → `MAX('spotify-2023'[streams])`  
- **Top Song Streams** → `CALCULATE(SUM('spotify-2023'[streams]), 'spotify-2023'[streams] = MAX('spotify-2023'[streams]))`  
- **Average Streams by Year** → `CALCULATE(AVERAGE('spotify-2023'[streams]), ALLEXCEPT('spotify-2023', 'spotify-2023'[released_year]))`  
- **Top Song vs. Average Percentage Change** →  
  ```DAX
  VAR x = DIVIDE([_Top_song_streams] - [_Avg_streams], [_Avg_streams])  
  RETURN IF(x > 0, FORMAT(x, "#.0%") & " " & UNICHAR(9650), FORMAT(x, "#.0%") & " " & UNICHAR(9660))  
