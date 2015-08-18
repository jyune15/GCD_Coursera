Getting and Cleaning Data in Data Science course of COURSERA_ COURSE PROJECT
====================================================================================

This is a code book describing the variables and summarizing I calculated.

#Describe the code and variables

1. Merges the training and the test sets to create on data set.

	1-1. read each data using read.table
	
	1-2. variables
	
		train:  traning set measurement data (7352 obs. and 561 variables)
		
		train.label:  labels for activities of training set (7352 obs. and 1 variable)
		
		train.subject:  no. for subjects of training set (7352 obs. and 1 variable)
		
		test:  test set measurement data (2947 obs. and 561 variables)
		
		test.label:  labels for activities of test set (2947 obs. and 1 variable)
		
		test.subject:  no. for subjects of test set (2947 obs. and 1 variable)
		
		dt:  mearged data set of train and test (10299 obs. and 561 variables)
		
		dt.label:  merged data set of train.label and test.label (10299 obs. and 1 variable)
		
		dt.subject: merged data set of train.subject and train.subject (10299 obs. and 1 variable)
		
2. Extracts only the measurements on the mean and standard deviation for each measurement

	2-1. read the "features.txt" which is names of each measurment as 'ft' (561 obs. and 2 variables)
	
	2-2. change column names of dt according to 'ft'("features.txt")
	
	2-3. take the indices('MandSD.index') for the measurements on the mean('mean') and standard deviation('std') using regular expression (66 length integer vector)
	
	2-4. make a new dataset('dt.MandSD') from 'dt' using the indices (10299 obs and 66 variables)
	
3. Uses descriptive activity names to name the activities in the data set

	3-1. read the "activity_labels.txt" which is indicating six activities of each label as 'activity' (6 obs. and 2 variables)
	
	3-2. labels for activities of merged data('dt.label') are replaced by the activity which the labels refer to.
	
4. Appropriately labels the data set with descriptive variable names. 

	4-1. 'Subject' for the name of 'dt.subject' 
	
	4-2. 'Activity' for the name of 'dt.label'
	
	4-3. Make the final merged data('dt.final') of the measurment for 'mean' and 'std' with subject and label variables(10299 obs and 68 variables)
	
5. From the data set in step 4(2-4), creates a second, independent tidy data set with the average of each variable for each activity and each subject.

	5-1. usig "dplyr" library
	
	5-2. make a data set('dt.final_avrByGr) of averages each measurement were calculated by groups of 'activity' and 'subject'
	
		6 activities and 30 subjects ---> 180 rows
		
	        numbers of each measurement(66), subjects and activities ---> 68 varialbes
	        
	5-3. Save the last data set in step 5 ('dt.final_avrByGr') as "tidy data_avr.txt".
	
