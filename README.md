# ExploratoryDataAnalysisWithPython
#import pandas and matplotlib libraries
import pandas as pd
import matplotlib.pyplot as plt

netflix_df = pd.read_csv('netflix_data.csv')
print(netflix_df[0:5])

netflix_subset = netflix_df[netflix_df['type'] == 'Movie']

netflix_movies = netflix_subset[['title', 'country', 'genre', 'release_year', 'duration']]

short_movies = netflix_movies[netflix_movies['duration'] < 60]  # Corrected variable name

print(short_movies[0:20])

colors = {
            'Children': 'red',
            'Documentaries': 'blue', 
            'Stand-Up': 'green', 
            'Other': 'purple'
    }
netflix_movies['color'] = netflix_movies['genre'].map(colors)

# Filter out rows where 'color' is NaN
netflix_movies = netflix_movies.dropna(subset=['color'])

fig = plt.figure(figsize=(12, 8))
plt.scatter('release_year', 'duration', data=netflix_movies, c=netflix_movies['color'])
plt.xlabel('Release_year')
plt.ylabel('Duration(min)')
plt.title('Movie Duration by Year of Release')

answer = 'yes', 'no', 'maybe'
