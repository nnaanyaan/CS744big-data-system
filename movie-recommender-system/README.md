# Movie-Recommender-System

## Overview
In this project, I built a movie recommender system based on Item Collaborative Filtering using Hadoop MapReduce in Java.

#### Data preprocessing

I preprocessed the original dataset in two steps:

Processing the data in each movie file into the following format: UserID, MovieID, Rating.
Merge 17770 movie files into one big input file since Hadoop is not good for dealing with lots of small files. 
And the big input file is the input of our recommender system. (apply Mapper-Join in MapReduce to solve the Out-of-Memory problem caused by the huge movie co-occurrence matrix.)


## Building Steps

* Divide data by user id
* Build co-occurrence matrix
* Normalize the co-occurrence matrix
* Build rating matrix
* Multiply co-occurrence matrix and rating matrix
* Generate recommendation list


## How to run

```
$hadoop com.sun.tools.javac.Main *.java
$jar cf recommender.jar *.class
$hadoop jar recommender.jar Driver /input /dataDividedByUser /coOccurrenceMatrix /normalizedMatrix /multiplicationMapperJoin /multiplicationSum /recommender
```

* args0: original dataset
* args1: output directory for DividerByUser job
* args2: output directory for coOccurrenceMatrixBuilder job
* args3: output directory for NormalizeCoOccurrenceMatrix job
* args4: output directory for MultiplicationMapperJoin job
* args5: output directory for MultiplicationSum job
* args6: output directory for RecommenderListGenerator job


