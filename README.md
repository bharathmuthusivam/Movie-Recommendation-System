# Movie-Recommendation-System
**Introduction**:
            
These files contain metadata for all 45,000 movies listed in the Full MovieLens Dataset. The dataset consists of movies released on or before July 2017. Data points include cast, crew, plot keywords, budget, revenue, posters, release dates, languages, production companies, countries, etc.

**Dataset path:**

kaggle datasets download -d rounakbanik/the-movies-dataset

**Approach**:

This is a content based movie recommendation system. After importing the basic packages and the dataset, data study and basic data preparation has been done like checking for duplicates & removing them, looking for null values, unique values, etc. 

Three data files has been used. movies_metadata.csv, keywords.csv, credits.csv.

Duplicates were checked on the basic of the 'id' field in all three files and found that there were 3 date values in the filed in movies dataset. They were found using RegEx and were dropped. keywords, credits files did not contain any NULL values. 

All 3 datasets were merged and only the significant fields to build the recommendation system were kept. Other fileds were dropped. Duplicates based on the 'title' and 'original_title' field were removed and null values were found only to be in the 'overview' filed. 

Information from the fileds were extracted using "ast.literal_eval" function by creating user-defined function according to the respective fields and the null values in 'overview' were not dropped as those records could still get significant information from other columns. So those null values were filled with empty spaces. Few recorsd of 'genres' and 'keywords' field also contained empty lists after extraction which were also not dropped for the same reason. 

Spaces were removed from the extracted words to avoid duplicate creation of tokens. Words in 'overview' filed was splitted and then all the significant filed were combined to get a single column. 

CountVectorizer has been used to create the tokens and the similarity matrix has been built using cosine_similarity. Finally a function has been created to build the recommendation system using the similarity matrix.

