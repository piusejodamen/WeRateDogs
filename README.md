## Reporting: Wragle_report


## Introduction

WeRateDogs is a Twitter account with the handle, @dog_rates. Dogs are rated and commented humorously. Typically, a denominator of 10 and a numerator often greater than 10 is used to rate each dog.

In this wrangling task, Jupyter Notebook and Python programming languages was used alongside several libraries including Pandas, Requests, Tweepy, Json, and Numpy among others. Data was gathered from several sources and in different formats. Notably, available archived data ('twitter-archive-enhanced.csv') was mined using Pandas dataframe. Thereafter, dataset containing image predictions – in Tab Separated Values (tsv) format - was mined via a weblink. Since additional data was necessary, Twitter API was used to retrieve relevant data such as the number of likes and retweets, as well as the date the tweet was posted.



## Wrangling Methodology

The Gather Data --> Assess Data --> Clean Data --> Store Data framework was adopted for this task. First, datasets are gathered from different sources, then assessed for quality and tidiness issues which are documented.  Thereafter, codes are used for more detailed assessment and cleaning of the data.


The various data was assessed for quality and tidiness issues before cleaning them. Visual and programmatic assessments were performed on the datasets for understanding of the data and identifying issues. It was noticed that some of the tweets were actually retweets, which could affect the quality of the data. It was also observed that some attributes were not needed, such as ‘retweeted_status_id’. Furthermore, ‘tweet_id’ was identified as the primary key as it uniquely identifies records in the three datasets. Hence, duplicate tweets were deleted as a quality control measure.

Typically, people give their dogs names! The dataset indicated the names of dogs in many cases. However, a quality issue noticed was obviously wrong/invalid names e.g “a”, “an”, “one”, “by”, e.t.c. These invalid names were replaced with “None”, to indicate that no name was entered. Furthermore, we programmatically searched each tweets for mention of the name of the dog being rated. Some names were discovered and used to replace “None” in the “name” column.

Data type is a critical data representation format that determines how data is processed. It is important that data are stored in their proper formats. This was a quality issued noticed in the datasets. For example, dates were stored as strings values rather than datetime datatypes, and tweet IDs were stored as Integer/float instead of strings. These abnormalities were cleaned and the most appropriate datatype were applied.

Tidiness issues are structural deformities or irregularities that can grossly affect the mining of insights from data. It is standard practice to identify and correct such issues. In our dataset, it was observed that the four dog stages were used as attributes/column headers. We opined that it is proper to have an attribute named “dog_stage” and the stage of the dog indicated, since a dog can only exist in one stage per time. Hence, after the restructuring, the attributes ('doggo', 'floofer', 'pupper', and 'puppo') were deleted. An important requirement was to indicate the development stage of the dogs as well as the name. It is noteworthy that a great number of the tweets did not indicate the stages of the dogs been rated.
Having three separate files loosely existing was a tidiness issue were corrected by merging the two datasets with the same tweet IDs i.e. the image_predictions and Tweet_Details datasets. The archived twitter-archive-enhanced did not match any tweet_ids used as primary key; as such it was not merged.


## Conclusion

Finally, both the merged dataset and the archived twitter-archive-enhanced were saved as a CSV file format.

The data revealed that among the four(4) dog stages mentioned in the tweets - namely Puppo, Doggo, Pupper, and Floofer, the dog stage that is most rated was the Pupper. Further analysis shows that the Floofer is the least dog stage of interest; it is least rated when compared to other dog stages.
