# CodeBook
Shawn Dong  
October 22, 2016  

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. 

For each record it is provided:
- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 81-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.

Here are the names of the variables: 
















```
##  [1] "subjectID"                        "activity"                        
##  [3] "TimeBodyAccMeanX"                 "TimeBodyAccMeanY"                
##  [5] "TimeBodyAccMeanZ"                 "TimeBodyAccStdX"                 
##  [7] "TimeBodyAccStdY"                  "TimeBodyAccStdZ"                 
##  [9] "TimeGravityAccMeanX"              "TimeGravityAccMeanY"             
## [11] "TimeGravityAccMeanZ"              "TimeGravityAccStdX"              
## [13] "TimeGravityAccStdY"               "TimeGravityAccStdZ"              
## [15] "TimeBodyAccJerkMeanX"             "TimeBodyAccJerkMeanY"            
## [17] "TimeBodyAccJerkMeanZ"             "TimeBodyAccJerkStdX"             
## [19] "TimeBodyAccJerkStdY"              "TimeBodyAccJerkStdZ"             
## [21] "TimeBodyGyroMeanX"                "TimeBodyGyroMeanY"               
## [23] "TimeBodyGyroMeanZ"                "TimeBodyGyroStdX"                
## [25] "TimeBodyGyroStdY"                 "TimeBodyGyroStdZ"                
## [27] "TimeBodyGyroJerkMeanX"            "TimeBodyGyroJerkMeanY"           
## [29] "TimeBodyGyroJerkMeanZ"            "TimeBodyGyroJerkStdX"            
## [31] "TimeBodyGyroJerkStdY"             "TimeBodyGyroJerkStdZ"            
## [33] "TimeBodyAccMagMean"               "TimeBodyAccMagStd"               
## [35] "TimeGravityAccMagMean"            "TimeGravityAccMagStd"            
## [37] "TimeBodyAccJerkMagMean"           "TimeBodyAccJerkMagStd"           
## [39] "TimeBodyGyroMagMean"              "TimeBodyGyroMagStd"              
## [41] "TimeBodyGyroJerkMagMean"          "TimeBodyGyroJerkMagStd"          
## [43] "FreqBodyAccMeanX"                 "FreqBodyAccMeanY"                
## [45] "FreqBodyAccMeanZ"                 "FreqBodyAccStdX"                 
## [47] "FreqBodyAccStdY"                  "FreqBodyAccStdZ"                 
## [49] "FreqBodyAccMeanFrequencyX"        "FreqBodyAccMeanFrequencyY"       
## [51] "FreqBodyAccMeanFrequencyZ"        "FreqBodyAccJerkMeanX"            
## [53] "FreqBodyAccJerkMeanY"             "FreqBodyAccJerkMeanZ"            
## [55] "FreqBodyAccJerkStdX"              "FreqBodyAccJerkStdY"             
## [57] "FreqBodyAccJerkStdZ"              "FreqBodyAccJerkMeanFrequencyX"   
## [59] "FreqBodyAccJerkMeanFrequencyY"    "FreqBodyAccJerkMeanFrequencyZ"   
## [61] "FreqBodyGyroMeanX"                "FreqBodyGyroMeanY"               
## [63] "FreqBodyGyroMeanZ"                "FreqBodyGyroStdX"                
## [65] "FreqBodyGyroStdY"                 "FreqBodyGyroStdZ"                
## [67] "FreqBodyGyroMeanFrequencyX"       "FreqBodyGyroMeanFrequencyY"      
## [69] "FreqBodyGyroMeanFrequencyZ"       "FreqBodyAccMagMean"              
## [71] "FreqBodyAccMagStd"                "FreqBodyAccMagMeanFrequency"     
## [73] "FreqBodyAccJerkMagMean"           "FreqBodyAccJerkMagStd"           
## [75] "FreqBodyAccJerkMagMeanFrequency"  "FreqBodyGyroMagMean"             
## [77] "FreqBodyGyroMagStd"               "FreqBodyGyroMagMeanFrequency"    
## [79] "FreqBodyGyroJerkMagMean"          "FreqBodyGyroJerkMagStd"          
## [81] "FreqBodyGyroJerkMagMeanFrequency"
```
