To Run the Code :
##
1. run cleaner.py to remove the posts for which tweets are not available  
   ./cleaner.py tweets_file.tsv  
the tweets_file contaions data in the following format: <tweetID>"\t"<ID>"\t"<label>"\t"<tweet>  
This creates the file 'cleanedtesting.data' with the same format  

Incase the above script gives _csv.Error: line contains NULL byte run the following command first on the tweets file  
iconv -c -f 'UTF-8' -t 'UTF-8//IGNORE' input-file | tr -d '\0' > output-file  

##
2. run preprocess.py for preprocessing of data  
   ./preprocess.py 0  
This creates preprocessedTesting and preprocessedTraining data files  
   ./preprocess.py 1  
This creates temppreprocessedTesting and temppreprocessedTraining data files which are used later for adding additional features  
##

3. run extendedFeatures.py to generate the additional features  
   ./extendedFeatures.py test/train  
This creates featureTraining/featureTesting data files in the following format: <tweet> <label> <positive> <negative> <neutral> <total_positive> <total_negative> <total_neutral> <negation> <hashtag> <special_characters(!*?)> <capitalized> <capsPositive> <capsNegative> <capsNeutral>  
	
##
4. run classification.py to classify the tweets  
   ./classification.py  
This will classify the tweets and prints the accuracy, confusion matrix, precision, recall and F1-score.  

