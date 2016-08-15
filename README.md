<h2><strong>“Segmentation_Test.py” file:</strong></h2><br/>
This python script tests the segmentation of the character images stored in the directory “Character_Document”. These are image files from which raw character image data are extracted for machine learning training.  This script just takes in one user input which stores the number of character documents in the directory “Character_Document”. The script generates the segmented images as shown below in figure 1 in the same directory. Machine learning classifier is used to recognize a character set of 87. Throughout the images the 87th parsed character of each set is tagged as shown below in figure 1. If the last character of the last of segmented image files “>” is given a tag of “87”, then it is understood that character segmentation throughout the character image files are done absolutely properly. If any other character is given the tag of “87” then there must be a segmentation mismatch most probably due to double segmentation of a single character.<br/><br/>


<h2><strong>“Classifier_Installation.py” file:</strong></h2><br/>
This python script helps the user to retrieve character image data; clean the raw data; and investigate the SVM classifiers using different C values, and finally installs the classifier file stored in directory “classifier”. The script contains seven major parts whose execution is controlled by user inputs from the command terminal. The descriptions of the seven parts or steps are given below:<br/>
<strong>1.</strong>	This portion parses the character images from the character image files stored in the directory “Character_Document” and store the character images which act as the training data in the directory “Characters”. The directory “Characters” is created if it not there.<br/>
<strong>2.</strong>	This portion extracts the character image data stored in “Characters”, cleans the data to make the data sparse, and then stores the data row-wise in the CSV file “training_data”. Execution of this step depends on if the raw character data is created in step 1.<br/>
<strong>3.</strong>	This portion extracts the character image data stored in “Characters”, cleans the data to make the data sparse, and then stores the data in the sqlite database file “CharacterData.sqlite” in the form of JSON. Execution of this step depends on if the raw character data is created in step 1.<br/>
<strong>4.</strong>	This portion trains SVM classifiers on the data from CSV file “training_data” using different C values. This portion takes the user input of start value, end value, and increment of the C values. Finally it generates an image file containing “Accuracy vs C value” plot. Execution of this step depends on if the CSV file containing data is created in step 2.<br/>
<strong>5.</strong>	This portion trains SVM classifiers on the data from sqlite database file “training_data” using different C values. This portion takes the user input of start value, end value, and increment of the C values. Finally it generates an image file containing “Accuracy vs C value” plot. Beware the script might generate memory error if the data file is too large. Execution of this step depends on if the sqlite database file containing data is created in step 3.<br/>
<strong>6.</strong>	This portion generates SVM classifier files in the directory “classifier” with a chosen value of C from the user, by extracting data from the CSV file “training_data”. The directory “classifier” is created if it not there. Execution of this step depends on if the CSV file containing data is created in step 2.<br/>
<strong>7.</strong>	This portion generates SVM classifier files in the directory “classifier” with a chosen value of C from the user, by extracting data from the sqlite database file “CharacterData.sqlite”. The directory “classifier” is created if it not there. Beware the script might generate memory error if the data file is too large. Execution of this step depends on if the sqlite database file containing data is created in step 3.<br/><br/>
This file gives the options to user to use either CSV file or sqlite database for data storage.<br/>

<h2><strong>“Segmentation.py” file:</strong></h2><br/>
This source code contains just the early version of my OCR fucntions needed for character segmentation from character extraction source files. The original source file in my work of OCR software contains much more updated, robust, and error tolerant functions; and contains much more functions than these. These functions are fine for character segmentation purpose as used by classifier installation file on character extraction source files, where each characters are finely separated by 3-4 spaces. In real world scenario characters are loosely separated and may be conjoining in many cases; character segmentation in such case needs further processing. 