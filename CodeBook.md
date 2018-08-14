# The data



# The variables


# Transformations performed
```Ruby
#1. Merges the training and the test sets to create one data set
setwd("C:/Users/liqia/Desktop/r code/3-project/UCI HAR Dataset")
library(dplyr)
library(data.table)

##Load train data
SubjectTrain = read.table('./train/subject_train.txt')
Xtrain = read.table('./train/X_train.txt')
Ytrain = read.table('./train/Y_train.txt')

##Load test data
SubjectTest = read.table('./test/subject_test.txt')
Xtest = read.table('./test/X_test.txt')
Ytest = read.table('./test/Y_test.txt')

##Bind train and test
X <- rbind(Xtrain, Xtest)
Y <- rbind(Ytrain, Ytest)
Subject <- rbind(SubjectTrain, SubjectTest)



#2. Extracts only the measurements on the mean and standard deviation for each measurement.
##The complete list of variables is stored in the second column of 'features.txt'
features <- read.table("./features.txt")
##find the **columns** in X that matches mean or std in **rows** features
MeanStrRow <-  grep("(mean|std)\\(\\)",features[,2])
##get mean and std in X
XMeanStd <- X[,MeanStrRow]
##name XmeanStd
names(XMeanStd) <- features[MeanStrRow,2]



#3. Uses descriptive activity names to name the activities in the data set
ActivityLables <- read.table("activity_labels.txt")
Y[,1] <- ActivityLables[Y[,1],2]



#4, Appropriately labels the data set with descriptive variable names.
##XMeanStd: data set, names are stored in features
names(XMeanStd) <- gsub('Acc','Acceleration',names(XMeanStd))
names(XMeanStd) <- gsub('GyroJerk','AngularAcceleration',names(XMeanStd))
names(XMeanStd) <- gsub('Gyro','AngularVelocity',names(XMeanStd))
names(XMeanStd) <- gsub('Mag','Magnitude',names(XMeanStd))
names(XMeanStd) <- gsub('^t','TimeDomain-',names(XMeanStd))
names(XMeanStd) <- gsub('^f','FrequencyDomain-',names(XMeanStd))
names(XMeanStd) <- gsub('BodyBody','Body',names(XMeanStd))

##Y: Activiy
names(Y) <- "Activity"

##: Subject
names(Subject) <- "Subject"



#5. Tidy data set with the average of each variable for each activity and each subject.
##Combine All Three, Creat raw complete data set
DataSet1 <- cbind(Subject,Y,XMeanStd)

##Calculate Mean
DataSet2 <- aggregate(DataSet1[,3:68],list(DataSet1$Subject, DataSet1$Activity),mean)
write.table(DataSet2, "TidyDataSet.txt")


```
