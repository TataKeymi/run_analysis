# run_analysis
# Project for Coursera Data Cleaning Course
# Assignment: Getting and Cleaning Data Course Project
###################################################################

#
# Data for the project:
# https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
#

####################################################################
# Purpose: 
# ========
# You should create one R script called run_analysis.R that 
#            does the following.
# 1) Merges the training and the test sets to create one data set.
# 2) Extracts only the measurements on the mean and standard deviation 
#            for each measurement.
# 3) Uses descriptive activity names to name the activities in the 
#            data set
# 4) Appropriately labels the data set with descriptive variable names.
# 5) From the data set in step 4, creates a second, independent 
#            tidy data set with the average of each variable for 
#            each activity and each subject.
####################################################################

####################################################################
# Working Assumptions:
# 1) The number of variables of interest is 33 
#              please refer features_info.txt (lines 10-29)
#    The mean and std of the 33 variables need to summarized
#              for each activity and subject.
#    
#    Specifically, the needed variables are: 
#    1.  tBodyAcc-mean()-X
#    2.  tBodyAcc-mean()-Y
#    3.  tBodyAcc-mean()-Z
#    4.  tBodyAcc-std()-X
#    5.  tBodyAcc-std()-Y
#    6.  tBodyAcc-std()-Z
#   41.  tGravityAcc-mean()-X
#   42.  tGravityAcc-mean()-Y
#   43.  tGravityAcc-mean()-Z
#   44.  tGravityAcc-std()-X
#   45.  tGravityAcc-std()-Y
#   46.  tGravityAcc-std()-Z
#   81.  tBodyAccJerk-mean()-X
#   82.  tBodyAccJerk-mean()-Y
#   83.  tBodyAccJerk-mean()-Z
#   84.  tBodyAccJerk-std()-X
#   85.  tBodyAccJerk-std()-Y
#   86.  tBodyAccJerk-std()-Z
#   121. tBodyGyro-mean()-X
#   122. tBodyGyro-mean()-Y
#   123. tBodyGyro-mean()-Z?
#   124. tBodyGyro-std()-X
#   125. tBodyGyro-std()-Y
#   126. tBodyGyro-std()-Z
#   161. tBodyGyroJerk-mean()-X
#   162. tBodyGyroJerk-mean()-Y
#   163. tBodyGyroJerk-mean()-Z
#   164. tBodyGyroJerk-std()-X
#   165. tBodyGyroJerk-std()-Y
#   166. tBodyGyroJerk-std()-Z
#   201. tBodyAccMag-mean()
#   202. tBodyAccMag-std()
#   214. tGravityAccMag-mean()
#   215. tGravityAccMag-std()
#   227. tBodyAccJerkMag-mean()
#   228. tBodyAccJerkMag-std()
#   240. tBodyGyroMag-mean()
#   241. tBodyGyroMag-std()
#   253. tBodyGyroJerkMag-mean()
#   254. tBodyGyroJerkMag-std()
#   266. fBodyAcc-mean()-X
#   267. fBodyAcc-mean()-Y
#   268. fBodyAcc-mean()-Z
#   269. fBodyAcc-std()-X
#   270. fBodyAcc-std()-Y
#   271. fBodyAcc-std()-Z
#   345. fBodyAccJerk-mean()-X
#   346. fBodyAccJerk-mean()-Y
#   347. fBodyAccJerk-mean()-Z
#   348. fBodyAccJerk-std()-X
#   349. fBodyAccJerk-std()-Y
#   350. fBodyAccJerk-std()-Z
#   424. fBodyGyro-mean()-X
#   425. fBodyGyro-mean()-Y
#   426. fBodyGyro-mean()-Z
#   427. fBodyGyro-std()-X
#   428. fBodyGyro-std()-Y
#   429. fBodyGyro-std()-Z
#   503. fBodyAccMag-mean()
#   504. fBodyAccMag-std()
#   516. fBodyBodyAccJerkMag-mean()
#   517. fBodyBodyAccJerkMag-mean()
#   529. fBodyBodyGyroMag-mean()
#   530. fBodyBodyGyroMag-std()
#   542. fBodyBodyGyroJerkMag-mean()
#   543. fBodyBodyGyroJerkMag-std()
#
# 2) Before merging the test and training data sets, the
#        activity and the subject has to be added to the data sets.
#        As there is no matching involved, rbind will be used to "merge"
#
# 3) Cleanup of the variable names in the features.txt file
#       (duplication of Body)
#
# 4) Give descriptive names to the activities 
#
# 5) Give descriptive names to variables
#
####################################################################
