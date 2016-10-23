# Getting & Cleanning Data
Shawn Dong  
October 22, 2016  



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

Extract data and Uses descriptive activity names 


```r
colindicator <- grepl("activityID", colnames(EntireData))|grepl("subjectID", colnames(EntireData))|grepl("mean", colnames(EntireData)) | grepl("std", colnames(EntireData))
newData <- EntireData[, colindicator]
colnames(activity_labels) <- c("activityID", "activity")
goalData <- merge(activity_labels, newData, by.x = "activityID")
goalData$activity <- factor(goalData$activity)
goalData <- goalData[, -1]
goalData <- goalData[, c(2,1, 3:81)]
```

Appropriately labels the data set with descriptive variable names.


```r
varNames <- names(goalData)
varNames <- gsub(pattern="^t",replacement="Time",x=varNames)
varNames <- gsub(pattern="^f",replacement="Freq",x=varNames)
varNames <- gsub(pattern="-?mean[(][)]-?",replacement="Mean",x=varNames)
varNames <- gsub(pattern="-?std[()][)]-?",replacement="Std",x=varNames)
varNames <- gsub(pattern="-?meanFreq[()][)]-?",replacement="MeanFrequency",x=varNames)
varNames <- gsub(pattern="BodyBody",replacement="Body",x=varNames)
names(goalData) <- varNames
```

Group the data


```r
# call reshape2 
library(reshape2)
# melt the data
moltenData <- melt(goalData, id.vars = c("subjectID", "activity"))
# take the mean based on the subjectID and activity type
DcastData <- dcast(moltenData, subjectID + activity ~ variable, fun.aggregate = mean)
TidyData <- DcastData[order(DcastData$subjectID, DcastData$activity),]
```

Output 


```r
write.table(TidyData, file = "Output - TidyData.txt", col.names = TRUE, row.names = FALSE)
```
