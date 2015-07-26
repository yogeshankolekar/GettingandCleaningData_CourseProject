# Introduction

The script `run_analysis.R`performs the 5 steps described in the course project's definition.

1. All the similar data is merged using the `rbind()` function i.e. those files having the same number of columns and referring to the same entities.
2. Only columns with the mean and standard deviation measures are taken from the dataset. After extraction they are given the correct names, taken from file `features.txt`.
3. As activity data is addressed with values 1:6, activity names and IDs from `activity_labels.txt` are substituted in the dataset.
4. In the final dataset, those columns with vague column names are corrected.
5. New dataset is created containing all the average measures for each subject and activity type (30 subjects * 6 activities = 180 rows). The output file is called `tidy_data.txt`, and uploaded to this repository.

# Variables

* `x_train`, `y_train`, `x_test`, `y_test`, `subject_train` and `subject_test` contain the data from the downloaded files.
* `x`, `y` and `subject` merge the previous datasets to further analysis.
* `features` contains the correct names for the `x_data` dataset, which are applied to the column names stored in `mean_and_std`, a numeric vector used to extract the desired data.
* A similar approach is taken with activity names through the `activities` variable.
* `all_data` merges `x`, `y` and `subject` in a big dataset.
* `averages` contains the relevant averages which will be later stored in a `tidy_data.txt` file. `ddply()` from the plyr package is used to apply `colMeans()` and ease the development.

# Identifiers
* subject - The ID of the test subject
* activity - The type of activity performed when the corresponding measurements were taken

# Activity Labels
* WALKING (value 1): subject was walking during the test
* WALKING_UPSTAIRS (value 2): subject was walking up a staircase during the test
* WALKING_DOWNSTAIRS (value 3): subject was walking down a staircase during the test
* SITTING (value 4): subject was sitting during the test
* STANDING (value 5): subject was standing during the test
* LAYING (value 6): subject was laying down during the test

# Variables
* mean and std for 't' & 'f' BodyAcc, BodyAccJerk, BodyGyro, BodyGyroJerk for (x, y, z)
* mean and std for 't' & 'f' BodyAccMag, GravityAccMag, BodyAccJerkMag, BodyAccJerkMag
