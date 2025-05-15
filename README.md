# TMDB Movie Data Scrapper

[![TMDB API](https://img.shields.io/badge/TMDB%20API-v3-blue)](https://developers.themoviedb.org/3)
[![Python](https://img.shields.io/badge/Python-3.6%2B-green)](https://www.python.org/)
[![Data Size](https://img.shields.io/badge/Dataset-1100%2B%20Movies-orange)](https://www.themoviedb.org/)

## 📋 Overview

This project is a robust data scrapper that collects comprehensive information about movies from The Movie Database (TMDB) API. The dataset spans from the earliest recorded films (1874) up to recent releases (2024), providing a rich historical record of cinema evolution, production details, popularity metrics, and financial data.

## 🎯 Purpose

The collected data can be used for various analytical and research purposes:

- Film history and evolution analysis
- Box office performance and ROI studies
- Genre popularity trends over time
- Production company dominance analysis
- Country-specific film industry research
- Movie rating and reception analysis
- Certification and content rating studies
- Data science projects and machine learning models
- Visualization projects examining film industry trends
- Academic research on cinema economics and cultural impact

## 🔍 Data Features

The dataset (`MovieData-Raw.csv`) contains extensive information about each movie, including:

- **Movie Identifiers**
  - TMDB ID
  - Title
  - Original Title

- **Release Information**
  - Release Date

- **Financial Data**
  - Budget
  - Revenue

- **Popularity Metrics**
  - Popularity Score
  - Runtime (minutes)
  - Vote Average (rating)
  - Vote Count (number of votes)

- **Content Attributes**
  - Adult Content Flag
  - Status (Released, Announced, etc.)
  - US Certification (PG, PG-13, R, etc.)

- **Categorization**
  - Genres (Action, Comedy, Drama, etc.)

- **Production Details**
  - Production Companies
  - Production Countries

## 🔧 Technical Implementation

The scrapper is built in Python and uses the following libraries:
- `tmdbsimple`: Core API wrapper for The Movie Database
- `pandas`: Data handling and CSV file operations
- `numpy`: Numerical processing
- `time`: Managing API rate limits and retries

The implementation follows these key processes:

1. **API Authentication**: Uses a TMDB API key to access the service
2. **Systematic Data Collection**: Iterates through years (1873-2024) to discover movies
3. **Pagination Handling**: Processes multiple pages of results per year
4. **Detailed Extraction**: Retrieves comprehensive movie data beyond basic discovery data
5. **Data Storage**: Incrementally saves data to CSV to prevent data loss
6. **Error Handling**: Implements retry mechanisms for API failures

## 📊 Data Collection Architecture

The data collection process follows this workflow:

1. Set up the DataFrame structure with appropriate columns
2. For each year from 1873 to 2024:
   - Query the TMDB Discover API to find movies released that year
   - Calculate the total number of pages to process
   - For each page of results:
     - Extract each movie's ID
     - Use the ID to make a detailed API request for complete movie information
     - Extract the US certification if available
     - Append the comprehensive movie data to the CSV file

## 💾 Data Structure

The dataset is stored in CSV format with the following columns:

| Column | Description |
|--------|-------------|
| id | TMDB unique identifier |
| title | Movie title (localized) |
| original_title | Original movie title |
| release_date | Official release date (YYYY-MM-DD) |
| budget | Production budget in USD |
| revenue | Box office revenue in USD |
| popularity | TMDB popularity score |
| runtime | Movie duration in minutes |
| vote_average | Average rating (0-10) |
| vote_count | Number of votes received |
| adult | Whether the movie is flagged as adult content |
| status | Release status (Released, In Production, etc.) |
| certification_US | US content rating (G, PG, PG-13, R, etc.) |
| genres | List of genre classifications |
| production_companies | Companies involved in production |
| production_countries | Countries where produced |

## 🧹 Data Cleaning Requirements

The raw dataset requires several cleaning operations before analysis:

1. **Handling Missing Values**: Many films have incomplete data (e.g., budget, revenue)
2. **JSON Parsing**: Genre, production companies, and countries are stored as JSON strings
3. **Date Normalization**: Converting release_date to proper datetime format
4. **Numeric Validation**: Ensuring budget/revenue values are properly formatted
5. **Deduplication**: Removing any duplicate entries
6. **Text Normalization**: Handling special characters in titles
7. **Currency Standardization**: Ensuring all financial values are in the same currency
8. **Outlier Detection**: Identifying and potentially addressing statistical outliers

## 🚀 Getting Started

### Prerequisites

- Python 3.6 or higher
- pip (Python package manager)

### Installation

1. Clone this repository
```bash
git clone https://github.com/prashantkoirala465/TMDB-Movie-Data-Scrapper.git
cd TMDB-Movie-Data-Scrapper
```

2. Create and activate a virtual environment (optional but recommended)
```bash
python -m venv myenv
# On Windows
myenv\Scripts\activate
# On macOS/Linux
source myenv/bin/activate
```

3. Install required packages
```bash
pip install -r requirements.txt
```

### Usage

To run the scrapper and collect movie data:

```bash
python scrapper.py
```

This will start collecting data from TMDB API and save it to `MovieData-Raw.csv`. The process may take several hours depending on your internet connection and API rate limits.

## 📝 Notes on API Usage

- The TMDB API has rate limits (40 requests per 10 seconds)
- The scrapper includes a retry mechanism with a 30-second wait on failures
- If you want to use your own API key, replace it in the `scrapper.py` file

## 📈 Sample Analysis Ideas

Here are some potential analyses you could perform with this dataset:

1. **Financial Performance Trends**
   - ROI analysis across decades
   - Budget vs. Revenue correlation studies
   - Identifying financially successful genres

2. **Temporal Patterns**
   - Film production volume by year/decade
   - Evolution of movie runtimes over time
   - Seasonal release patterns and success correlations

3. **Content Analysis**
   - Genre distribution and evolution
   - Adult content prevalence over time
   - Certification rating distribution by year

4. **Geographic Insights**
   - Production country shifts over film history
   - Regional genre preferences
   - International co-production trends

5. **Reception Analysis**
   - Vote count vs. vote average relationships
   - Popularity metrics analysis
   - Budget impact on audience ratings

## 🔗 Additional Resources

- [TMDB API Documentation](https://developers.themoviedb.org/3)
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Data Visualization with Matplotlib](https://matplotlib.org/)
- [Data Analysis with Seaborn](https://seaborn.pydata.org/)

## 📜 License

This project is for educational and research purposes. All data is sourced from TMDB API and is subject to their terms of use.

## 🙏 Acknowledgements

- Data provided by [The Movie Database (TMDB)](https://www.themoviedb.org/)
- Thanks to TMDB for their comprehensive API
- This project does not store or redistribute TMDB's content in a manner that would violate their terms of service

---

*Note: The data collected requires cleaning and processing before analysis. Consider implementing data cleaning pipelines to prepare the dataset for analytical use.* 
