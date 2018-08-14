# The data
The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained:
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

The data was downloaded from:
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip


# The variables Explained
## 1st column: Subject
Subject who performed the activity for each window sample. Its range is from 1 to 30

## 2nd column: Activity
6 activitys indentified:
* WALKING
* WALKING_UPSTAIRS
* WALKING_DOWNSTAIRS
* SITTING
* STANDING
* LAYING

## 3rd-68th column: Signals Captured
### Time Domain and Frequency Domain
* Time domain: signals were captured at a constant rate of 50 Hz. 
* Frequency Domain: fast Fourier Transform (FFT) was applied to some of these signals

### (Linear) Acceleration and Angular Velocity
The features selected for this database come from the accelerometer and gyroscope. The accelerometer captures acceletation, the gyroscope captures angular velocity. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. 

### Body and Gravity 
The acceleration signal was then separated into body and gravity acceleration signals using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

### Jerk
The body linear acceleration and angular velocity were derived in time to obtain Jerk signals .

### Magnitude
The magnitude of these three-dimensional signals were calculated using the Euclidean norm.

### XYZ
These signals were used to estimate variables of the feature vector for each pattern: '-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.


# Transformations performed
1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement.
3. Uses descriptive activity names to name the activities in the data set
4. Appropriately labels the data set with descriptive variable names.
5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

**For Steps performed, see `run_analysis.R`**
