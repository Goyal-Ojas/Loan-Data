# Loan-Data

Exercise 1 – Customer Loan Data with Pandas
1. Load the customer loan dataset "loan-data-v1.csv" as a Pandas DataFrame.
2. Filter the rows to keep only those that have "Days Delinquent" greater than or equal to 90.
3. Sort the rows in descending order by the "Days Delinquent" column.
4. Write the resulting (filtered and sorted) DataFrame with the columns "Name", "State", "Days
Delinquent", and "Years as Customer" to the output file "loan-data-output-v1.csv".
5. The first few lines of your output file should look like this:
You don't need to submit your output "loan-data-output-v1.csv" file.

Exercise 2 – Mobile App Database
Python Environment Setup
1. Download the "app-db.sqlite" file from Canvas and place it in the same directory (= folder) as your
submission .py file.
2. Your Spyder environment's "Files" tab must show both "app-db.sqlite" and your submission .py
files in the same directory.
3. Establish a connection with the database by creating a Connection object named conn as in the code
below.
WARNING: Modifying any part of the code below or the file path will result in ZERO points for this part
of the assignment regardless of correctness.
Instructions
The "app-db.sqlite" database file contains two SQL tables, app_info and app_stats, with columns as shown
below:
1. With the Connection object named conn, use the following SQL statement and retrieve the
app_info table from the "app-db.sqlite" database as a Pandas DataFrame.
2. With the Connection object named conn, use the following SQL statement and retrieve the
app_stats table from the "app-db.sqlite" database as a Pandas DataFrame.
3. Merge the two DataFrames from Steps 1 and 2 on the app_name column (= use the app_name
column as the join key). Run the .info() method on your merged DataFrame.
4. Get the first 5 rows of your merged DataFrame and assign it to a variable named q2ans1.
5. Generate a DataFrame with descriptive statistics of the numeric columns size, price, rating, reviews,
and installs of your merged DataFrame and assign it to a variable named q2ans2.
6. Generate a DataFrame with descriptive statistics of the category, type, and content_rating columns
of your merged DataFrame and assign it to a variable named q2ans3.
7. Generate a DataFrame with pairwise correlation of all numeric columns (size, price, rating, reviews,
and installs) of your merged DataFrame and assign it to a variable named q2ans4.
8. Get the counts (occurrences) of unique values of the category column of your merged DataFrame
and assign it to a variable named q2ans5.
9. Group your merged DataFrame by the unique values of column content_rating and generate a
DataFrame with the means of the other columns (size, price, rating, reviews, and installs) and assign it
to a variable named q2ans6.
10. Group your merged DataFrame by the unique values of column type and generate a DataFrame
with the means of the other columns (size, price, rating, reviews, and installs) and assign it to a variable
named q2ans7.
11. Group your merged DataFrame by the unique values of column category and generate a DataFrame
with the means (averages) of the other columns (size, price, rating, reviews, and installs) and assign it
to a variable named q2ans8.
12. From q2ans8, get the index (= row label) corresponding to the maximum value of each column of
q2ans8 and assign it to a variable named q2ans9.
13. Filter your merged DataFrame to contain only apps (= rows) that have greater than or equal to
100,000,000 installs. Write this filtered DataFrame to an Excel file named "most-installed-
apps.xlsx" with the argument index=False.

Exercise 3 - Text Analysis
This exercise aims to guide you through a text mining analysis using the techniques that we learnt so far.
Business requirement
You are asked to use Python to process and analyze app reviews. From the app review text file, you will need
to create a Python script that computes the most frequently used words in the app reviews. To visualize your
results, you will also generate a WordCloud of the app reviews.
Python Environment Setup
1. In Spyder, create your submission .py file in your choice of a working directory (= folder) on your
computer (follow the naming convention as described in the above Section 2.1).
2. Download the input app review text file "app-review.txt" to the same directory on your computer,
where your submission .py file is stored. Open the .txt (plain text) file to view its contents. You can
open it in Spyder or any other text editor (e.g., Mac TextEdit, Windows Notepad).
3. You will need to install and use a new Python library called wordcloud. You can install it using the
following code in your Spyder console — you only need to run it once. Do NOT include this code in
your submission .py file.
Please refer to this video for detailed instructions on how to install new libraries for you Python
environment: https://youtu.be/EI_xyppkWCA. If you encounter any issues with this, consult your
instructor for further assistance.
New Python Methods
Write a brief description about the following (which will be used in this assignment) as Python comments
in your submission .py file:
1. The specialized container datatype Counter from the collections library
2. The most_common() method of the Counter datatype.
Your description must include (1) what it does, (2) syntax, (3) what are the arguments and what they do.
Write your example code as well as its output as Python comments.
Instructions: Word Frequency
Your script must have the following components for the required solution:
1. Open your input data file "app-review.txt".
a. We will read the text file with pandas using the read_csv() function. Along with the text
file, we also pass separator as a new line character ('\n') because, for the app review file,
each review is separated by a new line (please try ‘\r\n’ if ‘\n’ doesn’t work). Set the header
argument to None to indicate that we want to use the default header. (Look at your
DataFrame, what is the default header?)
2. Combine the text in the DataFrame into a single string variable. (HINT: first extract the value part
using .values, then convert it to a list, and finally use the "join" method, see the function
remove_punctuation() below.)
3. Before computing frequencies of words, you will need to preprocess and clean the app review data
as follows:
a) Change all letters in the text to lowercase so that your code is not case-sensitive.
b) You will need to remove any punctuations from the text. For this, you have been provided with
the following remove_punctuations() function. In your own words, explain how this function
works. Write your explanation as Python comments. Your explanation must include how
the filter, lambda, and string join() works to produce the final return value new_str. Simply
saying "The function removes punctuations from a string" will not suffice.
Then use the remove_punctuations() function to remove any punctuations from the text.
4. Next you will need to tokenize (=separate) the entire text into individual words, where each word
(=token) is an individual Python string. Hint: you can use the string split() method to get a list of
tokenized words.
In this process, you will also need to remove what we call stopwords. Stopwords are the words that
do not add much meaning to a sentence, such as "the", "a", "is", "at", "which", "on", etc. These are
some of the most frequently used words in English text, but they can safely be ignored without
sacrificing the meaning of a sentence. Thus, stopwords are often filtered out before processing text
data.
The list of stopwords is provided to you as shown in the following starter code (the Python set
variable named stopwords). Use this variable to exclude stopwords in your tokenized list of words.
HINT: Let's say that you have a Python set variable named S. You can check if something is in or
not in S as shown in the example below:
5. Finally, compute the frequency of all words in the tokenized text by creating a Counter object using
the tokenized list of words. Then use its most_common() method to compute the top-5 most
frequent words in the text and print them out to the console.
