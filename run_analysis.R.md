# run_analysis.R
Shawn Dong  
October 13, 2016  



Download and read the data

```r
download.file("https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip", destfile = "./Data.zip")
unzip("Data.zip", exdir = "Data")
# extract the train data
x_train <- read.table("./Data/UCI HAR Dataset/train/X_train.txt")
y_train <- read.table("./Data/UCI HAR Dataset/train/Y_train.txt")
subject_train <- read.table("./Data/UCI HAR Dataset/train/subject_train.txt")
# extract the test data
x_test <- read.table("./Data/UCI HAR Dataset/test/X_test.txt")
y_test <- read.table("./Data/UCI HAR Dataset/test/Y_test.txt")
subject_test <- read.table("./Data/UCI HAR Dataset/test/subject_test.txt")
# read the features
features <- read.table("./data/UCI HAR Dataset/features.txt")
# read activity labels
activity_labels <- read.table("./data/UCI HAR Dataset/activity_labels.txt")
```

Assign column names


```r
# define train data
colnames(x_train) <- features[, 2]
colnames(y_train) <- "activityID"
colnames(subject_train) <- "subjectID"
# define test data
colnames(x_test) <- features[ , 2]
colnames(y_test) <- "activityID"
colnames(subject_test) <- "subjectID"
```

Merge data


```r
train <- cbind(y_train, subject_train, x_train)
test <- cbind(y_test, subject_test, x_test)
EntireData <- rbind(train, test)
```

Extract data


```r
colindicator <- grepl("activityID", colnames(EntireData))|grepl("subjectID", colnames(EntireData))|grepl("mean", colnames(EntireData)) | grepl("std", colnames(EntireData))
newData <- EntireData[, colindicator]
colnames(activity_labels) <- c("activityID", "activity")
goalData <- merge(activity_labels, newData, by.x = "activityID")
```

Group the data


```r
CleanData <- aggregate(.~subjectID+activityID, data = goalData, mean)
index <- order(CleanData$subjectID, CleanData$activityID, decreasing = FALSE)
TidyData <- CleanData[index, ]
```

Output 


```r
write.table(TidyData, file = "TidyData.txt", row.names = FALSE)
```
