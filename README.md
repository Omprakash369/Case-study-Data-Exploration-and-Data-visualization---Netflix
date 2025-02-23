# Case-study-Data-Exploration-and-Data-visualization->Netflix

# Problem Statement 
## Analyze the data and generate insights that could help Netflix in deciding which type of shows/movies to produce and how they can grow the business in different countries.

# Netflix 
Netflix is one of the most popular media and video streaming platforms. They have over 10000 movies or tv shows available on their platform, as of mid-2021, they have over 222M Subscribers globally. This tabular dataset consists of listings of all the movies and tv shows available on Netflix, along with details such as - cast, directors, ratings, release year, duration, etc.

## Schema 
***Show_id***: Unique ID for every Movie / Tv Show 

***Type***: Identifier - A Movie or TV Show

***Title***: Title of the Movie / Tv Show

***Director***: Director of the Movie

***Cast:*** Actors involved in the movie/show

***Country:*** Country where the movie/show was produced

***Date_added:*** Date it was added on Netflix

***Release_year:*** Actual Release year of the movie/show

***Rating:*** TV Rating of the movie/show

***Duration:*** Total Duration - in minutes or number of seasons

***Listed_in:*** Genre

***Description:*** The summary description.
*** Basic Exploration ***
``` python
import numpy as np
import pandas as pd
df = pd.read_csv('file.csv')

df.info()
df.isna().sum().reset_index()
df.groupby('type')['show_id'].count()
df.groupby(['type','rating'])['show_id'].count().sort_values(ascending=False).reset_index()
```
 ### Univariate and Bivariate Analysis

 ``` python
import plotly.express as px
pichart = px.pie(x, values='Count',names='rating',title='Distribution of content ratings')
pichart.show() ```


``` python
directorlist = pd.DataFrame()
directorlist['Director'] = data['director'].str.split(',',expand =True).stack()
group_director = directorlist.groupby('Director').size().reset_index(name ='TotalCounts')
goup_director = group_director[group_director['Director']!='not available']
groupdirector.sort_values(by=['TotalCounts'],ascending =False,inplace = True)
group_director  ```


```python
import seaborn as sns
import matplotlib.pyplot as pt
sns.barplot(x='Director', y = 'TotalCounts', data = top5)
pt.title('Top 5 Director on Netflix')
pt.show() ```


```python
cast = data[['cast','title','show_id']]
cast['cast'] = cast['cast'].str.split(',')
cast_explode = cast.explode('cast').reset_index(drop=True)
cast_explode.groupby(['cast'])['show_id'].count().sort_values(ascending = False)
```








