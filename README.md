# Peer-graded-Assignment-Getting-and-Cleaning-Data-Course-Project



Obtain the raw data sets and put them in the working directory (via Rstudio)
The following steps were performed in a PC running the operation system Window 8.1. The data cleaning processes were performed in Rstudio with R version 3.1.0

download the raw data from the following website: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

using the following R command to download the data:

     >setInternet2(TRUE)   
     >url_proj <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
     >download.file(urlproj, destfile="Dataset.zip", mode="wb")
unzip the raw data sets

     >unzip("Dataset.zip")
put the raw data sets in the selected working directory called "datacleaningproject" that is same name as in a repo in my Github account. (In other words, my working directory: "C:/Users/SJ/datacleaningproject")

     > getwd()

    [1] "C:/Users/SJ/datacleaningproject"
Create a tidy data via a R script called run_analysis.R
Preparation: data sets and script

The data sets and run_analysis.R must be in the working directory. It is based on one of the requirements this project: The code should have a file run_analysis.R in the main directory that can be run as long as the Samsung data is in your working directory. (see "Instructions and Requirements")

The input raw data for the run_analys.R are:

    ./train/X_train.txt, ./train/y_train.txt, subject_train.txt;
    ./test/X_test.txt, ./test/y_test.txt,  subjecct_test.txt;
    ./activity_labels.txt, ./features.txt
The output tidy data created from run_analysis.R are:

    ./tidy_average_data.txt (180 rows)
    ./combinedcleaningdata.txt (optional)
How the script run_analysis.R works via Rstudio

usage:

     > source("run_analysis.R") ## load the script
     > run_analysis() ##run the script
There are 5 main steps in run_analysis.R to process the raw data sets and create the tidy data set.

Step-0: Reminder -- to install special package "reshape2". It is necessary to install and to load the package "reshape2" before to perform any processes.

Step-1: Merges the training and the test data sets to create one data set (such as): Load and read the input raw sets; merge three pairs data set (e.g.: X_train.txt, X_test.txt; y_train.txt, y_test.txt; subject_train.txt, subject_text.txt) into three single data set via "rbind" function.

Setp-2: Extracts only the measurements on the mean and standard deviation for each measurement. This step is mainly done by the "grep" function by providing the key search patterns "-mean\(\)|-std\(\)".

    ++ column names from the data sets were changed into lower-case to avoid any uncessary typos
     (based on the intruction from the "Week4 slide-notes: Editing Text Variables" from 
     Coursera course Getting and Cleaning Data); characters "()" were replaced "" and
     characters "-" was replaced to "." via "gsub" function.
Step-3: Uses descriptive activity names to name the activities in the data set. This step is mainly to produce a one-column data frame called "joinlabel" containing descriptive activity names.

Step-4: Appropriately labels the data set with descriptive activity names. The step is mainly to combine three joined data frames into one data frame called "cleandata". This is the first cleaned data frame toward to the final tidy data set. An (optional/temporary) output file is created called "combinedcleandata.txt" just in case for an emergency.

Step-5: Creates a second, independent tidy data set with the average of each variable for each activity and each subject.

    + It is necessary to install and to load the package "reshape2" before to perform
    any processes.
    
    + The final tidy data frame called "tidydfrm" via "melt" function and then "dcast" function.
  
    + Finally, a file called "tidyDataSet.txt" was created via "write.table" function.
      This is the final output tidy processed data.
    
    + The detailed description of the "tidyDataSet.txt" and the given raw data set
      are in "CodeBook.md" file.
====================================================================================================


==========================================================================================================
