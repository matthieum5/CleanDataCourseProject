# Clean Data Course Project

The script run_analysis.R downloads and reads data txt files from the Human Activity Recognition dataset. Subject, Activity, and Measurement data are read in and then combined into single dataframes for both the training and test populations.The training and test dataframes are then combined into a single dataframe "allData"

## Create data directory and download data
if(!file.exists("./data")){dir.create("./data")}
fileURL <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
download.file(fileURL, destfile = "./data/rundata.zip", method = "curl")

## Read features data file for data column names
features <- read.csv("./data//UCI HAR Dataset/features.txt", 
                     sep = "", 
                     header = FALSE, 
                     stringsAsFactors = FALSE, 
                     col.names = c("Column", "Feature"))
varnames <- as.list(features$Feature)

## Read training datasets
activity <- read.csv("./data//UCI HAR Dataset/activity_labels.txt", 
                    sep = "", 
                    header = FALSE,
                    stringsAsFactors = FALSE,
                    col.names = c("Label", "Activity"))
labels <- as.list(activity$Activity)

trainSubject <- read.csv("./data//UCI HAR Dataset/train/subject_train.txt", 
                         header = FALSE, 
                         stringsAsFactors = FALSE, 
                         col.names = "Subject")
trainLabels <- read.csv("./data//UCI HAR Dataset/train/y_train.txt", 
                         header = FALSE, 
                         stringsAsFactors = FALSE, 
                         col.names = "Activity")
trainData <- read.csv("./data//UCI HAR Dataset/train/X_train.txt", 
                      sep = "", 
                      header = FALSE, 
                      stringsAsFactors = FALSE)
colnames(trainData) <- varnames
train <- cbind(trainSubject, trainLabels, trainData)

## Read test data sets
testSubject <- read.csv("./data//UCI HAR Dataset/test/subject_test.txt", 
                        sep = "", 
                        header = FALSE, 
                        stringsAsFactors = TRUE, 
                        col.names = "Subject")
testLabels <- read.csv("./data//UCI HAR Dataset/test/y_test.txt", 
                        sep = "", 
                        header = FALSE, 
                        stringsAsFactors = TRUE, 
                        col.names = "Activity")
testData <- read.csv("./data//UCI HAR Dataset/test/X_test.txt", 
                     sep = "", 
                     header = FALSE, 
                     stringsAsFactors = FALSE)
colnames(testData) <- varnames
test <- cbind(testSubject, testLabels, testData)

## Combine the train and test datasets
allData <- rbind(train, test)


"allData" is subset to only the varaibles containing mean or std acceleration measurements, and reordered by Subject designation.

## Select data columns for mean and std, reorder data by Subject
exData <- allData[grepl("Subject|Activity|mean\\()|std\\()", names(allData))]
exData <- exData[order(exData$Subject),]

"exData" Activity factors are converted to descriptive labels.

## Convert Subject and Activity to factors, relabel Activity factors
exData$Subject <- as.factor(exData$Subject)
exData$Activity <- as.factor(exData$Activity)
exData$Activity <- revalue(exData$Activity, c("1" = "Walking", 
                                              "2" = "Walking_Upstairs", 
                                              "3" = "Walking_Downstairs",
                                              "4" = "Sitting", 
                                              "5" = "Standing", 
                                              "6" = "Laying"))

"exData" is melted and recast to dataframe "meanData" to summarize mean values of variable by subject and by activity

## Reshape dataset to tall and skinny form, and recast to summarize 
## mean measurement values
exnames <- colnames(exData[3:68])
meltData <- melt(exData, id = c("Subject", "Activity"), measure.vars = exnames)
meanData <- dcast(meltData, Subject+Activity~variable, mean)
