# Spotify Dataset - Data Analysis

### Random

## 1. Background

Spotify is the global leader in the streaming music sector. Spotify datasets is ideal in analyzing track trends, track popularity, etc. Spotify music datasets have become one of the most prominent datasets in the data science field for learning predictive modeling.

The author created this repo for its portfolio, at the same time, to test functions relative to data analysis.
### 1.1 Data Collection

The dataset is from Kaggle. Here is the link to the [Spotify Dataset](https://www.kaggle.com/datasets/lehaknarnauli/spotify-datasets). There are two (2) datasets we have used for this project - Tracks and artists dataset. The following are its column feature fromt he data:

#### Main Features
- track_id and artist_id: unique identifier for each track and artist used by Spotify (randomly generated alphanumeric string)
- track_name and artist_name: track name
- popularity: song popularity score as of March 2021 on a normalized scale [0-100] where 100 is the most popular
- duration_ms: duration of track in milliseconds
- explicit: true or false if the song contains explicit content.
artists: name of the main artist
- release_date: when the album was released (date format: yyyy/mm/dd)

#### Sub Features
- danceability: describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.
- energy: measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy.
- key: The estimated overall key of the track. Integers map to pitches using standard Pitch Class notation. E.g. 0 = C, 1 = C♯/D♭, 2 = D, and so on. If no key was detected, the value is set to -1.
loudness: The overall loudness of a track in decibels (dB). Values typical range between -60 and 0 db.
mode: Mode indicates the modality (major=1 or minor=0) of a track, the type of scale from which its melodic content is derived.
- speechiness: measures from 0.0 to 1.0 and detects the presence of spoken words in a track. If the speechiness of a song is above 0.66, it is probably made of spoken words, a score between 0.33 and 0.66 is a song that may contain both music and words, and a score below 0.33 means the song does not have any speech.
- acousticness: confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic
instrumentalness: measure from 0.0 to 1.0 and represents the amount of vocals in the song. The closer it is to 1.0, the more instrumental the song is.
- liveness: likelihood measure from 0.0 to 1.0 and indicates the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live.
valence: A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track.
- tempo: The overall estimated tempo of a track in beats per minute (BPM)
- time_signature: An estimated overall time signature of a track. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure).


### 1.2 Questions and Hypothesis

- Does the artist popularity have a direct correlation on how popular the track will be?
- What features of the track should the artist be concern about?

## 2. Approach and Analysis
### 2.1 Project Stages

Here, we created a workflow and project stages to make sure that our analysis is based of our target or main criteria. For this dataset, popularity is our main criteria and we will aligned our analysis relative to that feature.

| Stages | Output |
|---|---|
| 0. Basic Exploration of Dataset. | Explore the basics of pandas library; checking the information, describe, datatypes, columns, etc. |
| 1. Continue to Explore of the Dataset. | Here we explore further in-depth, given the Spotify Dataset. This includes and not limited to the following: <br> - Checking the null, missing and 0 values <br> - Checking the histogram or distribution of each feature column <br> - Creating pandas-profiling html to automate exploratory data analysis. <br> - Checking for the correlation for each column. |
| 2. Transforming the dataset. | - Initial process would include converting the csv file to parquet file; this would reduce the file size by half. <br> - Removing data points that has null or 0 on the main criteria column (popularity and followings). <br> - Removing data points that is heavily skewed based on its histogram. <br> - Renaming the columns between the 2 dataset so that artist and track identifiers are separate. <br> - Merging the 2 datas based on the artist_id. <br> - Standard preprocessing such as sorting and resetting the index by the main criteria and transforming data based on its proper datatype. |
| 3. Main Criteria | The output is an analysis based on the main criteria, popularity, of the project. The analysis must be based of the main target or criteria of the project, therefore aligning all the graphs, reports and data output to the target. For the project, sample output would be... |
| 4. Feature Data | Afterwards, we focus on the other feature of the dataset - relative to the popularity. |


## 3. Result

### 3.1 Results and Output per stage
In this repo, we will only be highlighting the main points and visualization per stage.

#### Exploring Dataset
With the matrix diagram, we were able to analyze values that has null, zero and nan in the entire dataset, plus the location of those values. Another good visualization for this stage, histogram of all the features within the dataset. This reveals the skewness of the distribution. For example in the popularity histogram, there is a lot of the datapoints with 0 values within the column.

![alt text](output/01-data_exploration/2023127-TracksData_Popularity_CategoryHist.png)
![alt text](output/01-data_exploration/2023127-TracksData_Hist.png)

#### Transforming Dataset
Joining the two datasets, artists and tracks data, took a long time to process with pandas library. Although joining two dataframes is necessary to understand the relationship between artist popularity and the track popularity.

#### Main Analysis

Although we did explore the distribution in the first stages of the workflow, we still created distribution for each main column to make sure that values are not skewed towards one or a few values in the column distribution. 

![alt text](output/03-analysis_main/202322-TracksData_Hist.png)
![alt text](output/03-analysis_main/2023128-TracksData_Track_Popularity_CategoryHist.png)

Moreover, there is a direct trend between the artist popularity or artist followers over track popularity. That means - given the current artist is well-knowned, then as analyzed, there is a bigger chance that the track will also be as popular.

![alt text](output/03-analysis_main/202322-TracksData_BoxPlot_Artist_Mean_Popularity&Track_Popularity.png)
![alt text](output/03-analysis_main/202322-TracksData_LinePlot_Artist_Mean_Popularity&Track_Popularity.png)

Although, there might be also be a possibility that the dataset is biased towards the newer tracks, given the dataset viewer is at a younger generation. This is only an assumption based on this chart.

![alt text](output/03-analysis_main/Popularity_with_year.png)

#### Features Check
The top 10% and 25% of the tracks in the datasets has high energy, high danceability and high valence.

![alt text](output/04-analysis_feature/2023116-TracksData_PolarFeatureByCount.png)

### 3.2 Takeaways and Recommendation
- Processing list of lists within pandas library is not a scalable solution, especially given a large datasets. Explore polars in pyspark in python as alternative.
- Criteria should be emphasize at the early stage of the analysis. It gives the direction for the reports, datas and graphs to extract and process. In here, we emphasize on the tracks popularity; given the popularity what features are significantly higher.


## 4. Reference
- https://www.kaggle.com/code/vhtrieu/spotify-track-popularity-analysis-and-prediction
