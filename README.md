# Experiment-6---Implementation-of-Semantic-Analysis

## Aim : Construct a python program to read a text from a file.Identify the verbs from the text file and provide synonyms for all verbs using Natutal Language Processing 

## Algorithm:
1.Import the necessary libraries: nltk and wordnet.

2.Define a function get_verbs(sentence) to identify verbs in a given sentence using part-of-speech tagging.

3.Define a function get_synonyms(word) to get synonyms for a given word using the WordNet corpus.

4.Define a function read_text_file(file_path) to read text from a file and return the content as a string.

5.In the main program:
Set the file_path variable to the path of the input text file.
Read the text from the file using the read_text_file() function.
Tokenize the text into sentences using the sent_tokenize() function from the nltk library.
Initialize an empty list all_verbs to store all identified verbs.
Initialize an empty dictionary synonyms_dict to store the synonyms for each verb.
Iterate over each sentence:
Call the get_verbs() function to identify verbs in the sentence.
Append the identified verbs to the all_verbs list.
For each verb, call the get_synonyms() function to get its synonyms and store them in the synonyms_dict dictionary.
Print the verbs and their synonyms.
6.Execute the main program.

## Program:



## Output:

## Result
