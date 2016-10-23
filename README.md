# README

# How files in the repo works

The "Output - TidyData.txt" is the output of the R code file "run_analysis.R.md". The "CodeBook.md" is used to describe the variables. 

Since you will understand "Output - TidyData.txt" and "CodeBook.md" once you see them, I will walk you through my R code here.

# Regarding the "Output - TidyData.txt"

If you want to have a best view of it, please put my R code into your RStudio and then enter:

x <- read.table(TidyData, header = TRUE)

View(x)

Note: TidyData is the variable to store my end result in my R code. 

# R code

The code basically did the following things: 

1. Download the data from the url and read the data

2. Merges the training and the test sets to create one data set.

3. Extracts only the measurements on the mean and standard deviation for each measurement.

4. Uses descriptive activity names to name the activities in the data set

5. Appropriately labels the data set with descriptive variable names.

6. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
