Getting and Cleaning Data Course Project

Smartphone triaxial acceleration measurement data for training and test populations, sourced from following files:

subject_train.txt

y_train.txt

X_train.txt

subject_test.txt

y_test.txt

X_test.txt

features.txt

activity_labels.txt

Subject files contain numeric designation of human subjects (1-30)

X files contain acclerometer measurement values (561 measurement variables), listed in file features.txt

Y files contain human activity designations 1-6, listed in file activity_labels.txt

Subject, Activity, and Measurements are combined into single dataframe for each subject population (i.e. "trainData" and "testData").

Training and Test data frames are combined into single data frame "allData".

"allData" is subset to mean and std measurements only in "exData" data frame (66 measurement variables), and sorted in descending order by Subject designation.

"exData" is melted and recast in data frame "meanData" summarizing the mean value of measurements for each activity by each subject.

The final dataset "meanData" (dim 180 x 68) contains the following variables:

ID Variables:

[[1]]
[1] "Subject"

[[2]]
[1] "Activity"

Measurement Variables:

[[3]]
[1] "MeanBodyAccelerationX"

[[4]]
[1] "MeanBodyAccelerationY"

[[5]]
[1] "MeanBodyAccelerationZ"

[[6]]
[1] "MeanBodyAccelerationX"

[[7]]
[1] "MeanBodyAccelerationY"

[[8]]
[1] "MeanBodyAccelerationZ"

[[9]]
[1] "MeanGravityAccelerationX"

[[10]]
[1] "MeanGravityAccelerationY"

[[11]]
[1] "MeanGravityAccelerationZ"

[[12]]
[1] "MeanGravityAccelerationX"

[[13]]
[1] "MeanGravityAccelerationY"

[[14]]
[1] "MeanGravityAccelerationZ"

[[15]]
[1] "MeanBodyAccelerationJerkX"

[[16]]
[1] "MeanBodyAccelerationJerkY"

[[17]]
[1] "MeanBodyAccelerationJerkZ"

[[18]]
[1] "MeanBodyAccelerationJerkX"

[[19]]
[1] "MeanBodyAccelerationJerkY"

[[20]]
[1] "MeanBodyAccelerationJerkZ"

[[21]]
[1] "MeanBodyGyroX"

[[22]]
[1] "MeanBodyGyroY"

[[23]]
[1] "MeanBodyGyroZ"

[[24]]
[1] "MeanBodyGyroX"

[[25]]
[1] "MeanBodyGyroY"

[[26]]
[1] "MeanBodyGyroZ"

[[27]]
[1] "MeanBodyGyroJerkX"

[[28]]
[1] "MeanBodyGyroJerkY"

[[29]]
[1] "MeanBodyGyroJerkZ"

[[30]]
[1] "MeanBodyGyroJerkX"

[[31]]
[1] "MeanBodyGyroJerkY"

[[32]]
[1] "MeanBodyGyroJerkZ"

[[33]]
[1] "MeanBodyAccelerationMag"

[[34]]
[1] "MeanBodyAccelerationMag"

[[35]]
[1] "MeanGravityAccelerationMag"

[[36]]
[1] "MeanGravityAccelerationMag"

[[37]]
[1] "MeanBodyAccelerationJerkMag"

[[38]]
[1] "MeanBodyAccelerationJerkMag"

[[39]]
[1] "MeanBodyGyroMag"

[[40]]
[1] "MeanBodyGyroMag"

[[41]]
[1] "MeanBodyGyroJerkMag"

[[42]]
[1] "MeanBodyGyroJerkMag"

[[43]]
[1] "MeanBodyAccelerationX"

[[44]]
[1] "MeanBodyAccelerationY"

[[45]]
[1] "MeanBodyAccelerationZ"

[[46]]
[1] "MeanBodyAccelerationX"

[[47]]
[1] "MeanBodyAccelerationY"

[[48]]
[1] "MeanBodyAccelerationZ"

[[49]]
[1] "MeanBodyAccelerationJerkX"

[[50]]
[1] "MeanBodyAccelerationJerkY"

[[51]]
[1] "MeanBodyAccelerationJerkZ"

[[52]]
[1] "MeanBodyAccelerationJerkX"

[[53]]
[1] "MeanBodyAccelerationJerkY"

[[54]]
[1] "MeanBodyAccelerationJerkZ"

[[55]]
[1] "MeanBodyGyroX"

[[56]]
[1] "MeanBodyGyroY"

[[57]]
[1] "MeanBodyGyroZ"

[[58]]
[1] "MeanBodyGyroX"

[[59]]
[1] "MeanBodyGyroY"

[[60]]
[1] "MeanBodyGyroZ"

[[61]]
[1] "MeanBodyAccelerationMag"

[[62]]
[1] "MeanBodyAccelerationMag"

[[63]]
[1] "MeanBodyBodyAccelerationJerkMag"

[[64]]
[1] "MeanBodyBodyAccelerationJerkMag"

[[65]]
[1] "MeanBodyBodyGyroMag"

[[66]]
[1] "MeanBodyBodyGyroMag"

[[67]]
[1] "MeanBodyBodyGyroJerkMag"

[[68]]
[1] "MeanBodyBodyGyroJerkMag"

