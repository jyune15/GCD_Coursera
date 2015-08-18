Getting and Cleaning Data in Data Science course of COURSERA_ COURSE PROJECT

This is for describing how the script(run_analysis.R) works and as a code book describing the variables.

1. Instruction for executing "run_analysis.R"
	1) Download the data from website (https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)
	2) Load the "run_analysis.R" file on your R
	3) Setting the working directory
	4) Please run the codes of the file
	5) At the end of the code, you will get the file "tidy data_avr.txt".

2. Describe the code and variables
	2-1. Merges the training and the test sets to create on data set.
		2-1-1. read each data using read.table
		2-1-2. variables
			train:  traning set measurement data (7352 obs. and 561 variables)
			train.label:  labels for activities of training set (7352 obs. and 1 variable)
			train.subject:  no. for subjects of training set (7352 obs. and 1 variable)
			test:  test set measurement data (2947 obs. and 561 variables)
			test.label:  labels for activities of test set (2947 obs. and 1 variable)
			test.subject:  no. for subjects of test set (2947 obs. and 1 variable)
			dt:  mearged data set of train and test (10299 obs. and 561 variables)
			dt.label:  merged data set of train.label and test.label (10299 obs. and 1 variable)
			dt.subject: merged data set of train.subject and train.subject (10299 obs. and 1 variable)
	2-2. Extracts only the measurements on the mean and standard deviation for each measurement
		2-2-1. read the "features.txt" which is names of each measurment as 'ft' (561 obs. and 2 variables)
		2-2-2. change column names of dt according to 'ft'("features.txt")
		2-2-3. take the indices('MandSD.index') for the measurements on the mean('mean') and standard deviation('std') using regular expression (66 length integer vector)
		2-2-4. make a new dataset('dt.MandSD') from 'dt' using the indices (10299 obs and 66 variables)
	2-3. Uses descriptive activity names to name the activities in the data set
		2-3-1. read the "activity_labels.txt" which is indicating six activities of each label as 'activity' (6 obs. and 2 variables)
		2-3-2. labels for activities of merged data('dt.label') are replaced by the activity which the labels refer to.
	2-4. Appropriately labels the data set with descriptive variable names. 
		2-4-1. 'Subject' for the name of 'dt.subject' 
		2-4-2. 'Activity' for the name of 'dt.label'
		2-4-3. Make the final merged data('dt.final') of the measurment for 'mean' and 'std' with subject and label variables(10299 obs and 68 variables)
	2-5. From the data set in step 4(2-4), creates a second, independent tidy data set with the average of each variable for each activity and each subject.
		2-5-1. usig "dplyr" library
		2-5-2. make a data set('dt.final_avrByGr) of averages each measurement were calculated by groups of 'activity' and 'subject'
			6 activities and 30 subjects ---> 180 rows
		        numbers of each measurement(66), subjects and activities ---> 68 varialbes
		2-5-3. Save the last data set in step 5 ('dt.final_avrByGr') as "tidy data_avr.txt".
