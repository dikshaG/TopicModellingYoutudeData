Topic Modeling on you-tube data
The input dataset can be accessed from: https://www.idiap.ch/dataset/youtube-personality

PROBLEM STATEMENT
------------------
Given the transcripts of You-tube Vlogs, Identify the topic on which the person is speaking.
Vlogs are videos in which a person debates on a topic same as tweets but in the form of video.
WCPR dataset is used which included 404 transcripts of Vlogers. Each transcript consists of about 500 words.
The YouTube personality dataset consists of a collection of behavioral features. There is no content-related
restriction and the language used in the videos is natural and diverse.

APPROACH
--------
Each profile of YouTube data is accessed by java file system and processed (text transformation) for topic 
mining using following steps:
 1) Tokenization by splitting the text and Lowercasing of the text is done.
 2) Accumulated a list of stop-words (useless words in article) for removing stop-words.
 3) Removal of noise words.
 4) Stemming using porter algorithm.
 5) Creation of tf-idf matrix. As I had to predict the topic for each document, so tf-idf is calculated for
    each docement.
 6) All the extracted important words are sorted in increasing order of tf-idf.
 7) Wikipedia topics list is used for finding the appropriate topic.
 8) For each document, all the important words are compared with the list of topics i.e. with each match, 
    the tf-idf will be added to the score of the topic and the largest weight topic will be assigned to the
    document.

CLASSES CREATED 
----------------
1) globals- This file contains all the shared variables declarations.
2) mainfile- This file contains the main. It calls all the other modules.
3) preprocess- All the preprocessing of data i.e. text transformation is done in this class.
4) Stemmer- This class contains the implementation of porter stemmer algorithm for stemming.
5) docmatrix- This file contains the code for calculating tf-idf and score for each document. 
	      It also have the code for detemining common male and female topics.
6) ValueComparator- This class is used for sorting the topics accorinf to tf-idf values.

EXECUTE THE PROGRAM
--------------------

1) Save your directory containing the sample files in 'TopicModelling' folder.
2) Change the name of the directory in "globals.java" to your directory name. Currently folder name is 'dataset'.
3) Run mainfile.java as java application (using eclipse or any java IDE).

RESULTS
-------
1) The output contains the video name and it's corresponding list number. As the topic can be any word from a
   list of related keywords, each video has a list number as a result for appropriate topic.
2) The score tells about the strength of topic list generated. Higher the score better the result list. This 
   score is calculated by adding tf-idfs of those words that can be related to the list of topics.
3) Best word can be used as an appropriate topic but in some cases the best word can be any 1 from the resultant
   list.The "Best word" is the word that contributed the most towards calculating the score for the resultant 
   topic list.
4) With the input decribing the gender of the speaker and the resultant topic list, the male common topics and
   female common topics are estimated. The results lists the topic list number and number of male or female who
   talked about this topic.

DRAWBACKS AND FUTURE WORK
-------------------------
1) This approach doesn’t perform any contextual analysis. 
2) This will fail for very large number of documents. Structures can be modified or system can be parallelized
   to overcome this problem.
To avoid both, LDA-probabilistic approach can be used.

RESOURCES
----------
1) http://tartarus.org/martin/PorterStemmer/java.txt
2) http://www.lextek.com/manuals/onix/stopwords1.html
3) http://programminghistorian.org/lessons/topic-modeling-and-mallet
4) http://gibbslda.sourceforge.net/



