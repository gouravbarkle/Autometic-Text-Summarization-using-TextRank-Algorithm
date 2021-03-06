# What is Text Summarization?

Text Summarization is one of the most challenging and interesting problems in the field of Natural Language Processing (NLP).
It is basically creating a summary of a long text given i.e to extract core ideas of a document/essay/paragraph or any other text form and arrange those ideas in such an order that makes sense.
Using the process of text summarization, we can have a concise and meaningful summary of text from multiple text resources such as books, news articles, blog posts, research papers, emails, and tweets.


# What’s the need for text summarization?

Today, our world is producing a huge amount of data on the daily basis.
International Data Corporation (IDC) projects that the total amount of digital data circulating annually around the world would sprout from 4.4 zettabytes in 2013 to hit 180 zettabytes in 2025.
With such a big amount of data circulating in the digital space, there is need to automatically shorten longer texts and deliver accurate summaries. 


# Approaches to automatic summarization

Extraction-based summarization
The extractive text summarization technique involves pulling keyphrases from the source document and combining them to make a summary. 
The extraction is made according to the defined metric without making any changes to the texts.
Although sometimes the summary can be grammatically strange when summarized with using extraction based method.  

Abstraction-based summarization
The abstraction technique entails paraphrasing and shortening parts of the source document.
The abstractive text summarization algorithms create new phrases and sentences that relay the most useful information from the original text — just like humans do.
When abstraction is applied for text summarization in deep learning problems, it can overcome the grammar inconsistencies of the extractive method.


# Understanding the TextRank Algorithm

Before getting started with the TextRank algorithm, there’s another algorithm which we should become familiar with – the PageRank algorithm.
PageRank algorithm is the inspiration of TextRank algorithm, PageRank is used primarily for ranking web pages in online search results.
Let’s quickly understand the basics of this algorithm with the help of an example.

# PageRank Algorithm
Suppose we have 4 web pages — w1, w2, w3, and w4. These pages contain links pointing to one another. Some pages might have no link – these are called dangling pages.

1. Web page w1 has links directing to w2 and w4
2. w2 has links for w3 and w1
3. w4 has links only for the web page w1
4. w3 has no links and hence it will be called a dangling page

PageRank assumes that the rank of a webpage W depends on the importance of a webpage suggested by other web pages in terms of links to the page i.e if a webpage ‘X’ has a link to webpage ‘W’, ‘X’ contributes to the importance of ‘W’.

n order to rank these pages, we would have to compute a score called the PageRank score. This score is the probability of a user visiting that page.
The initialization of the probabilities is explained in the steps below: 

1. Probability of going from page i to j, i.e., M[ i ][ j ], is initialized with 1/(number of unique links in web page wi)
2. If there is no link between the page i and j, then the probability will be initialized with 0
3. If a user has landed on a dangling page, then it is assumed that he is equally likely to transition to any page. Hence, M[ i ][ j ] will be initialized with      1/(number of web pages)

Finally, the values in this matrix will be updated in an iterative fashion to arrive at the web page rankings.

# But how is TextRank associated with Pagerank?
TextRank also uses the same logic as in PageRank but with some changes:
1. Text sentences are used in place of WebPages.
2. The similarity matrix for index [A, B] is filled with similarity values between sentences A & B rather than 1/total_links from Page B to A.
    a. That similarity values could be depend on the count of the maximum common words in between two sentences or cosine similarity between two sentences. 
    b. Where the term cosine similarity refers to the similarity between two vectors measured by the cosine of the angle between two vectors and determines              whether two vectors are pointing in roughly the same direction,as word embedding gives the vector representation of words.

# Problem Statement
A system design that could prepare a bullet-point summary by scanning through multiple articles.
This is essentially a Single-Domain-Multiple-Documents Summarization task,i.e., we will take multiple articles as input and generate a single bullet-point summary. 

The text summarization approach we will consider here will be extraction-based. 

# Dataset Description 
the dataset we are using here for this problem is a CSV file that contains four different sources attributes defined as follows :

article id
article title
article text
article source

But the centre of attraction for our problem will be the third attribute i.e, article text.
We will consider the article text from all rows and combine them all to summarize into one. 

# Dataset Preprocessing 
Import CSV data into pandas dataframe.
Consider article text attribute and convert them all into a list of sentences. 
Remove punctuations, numbers and special characters.
Make alphabets lowercase.
Get rid of the stopwords present in the sentences.

Finally, we will have a list of clean sentences to create vectors for sentences in our data with the help of the GloVe word vectors.

# Implementation of the TextRank Algorithm

Steps to follow after preprocessing phase:
Representing sentences into vectors using the word embedding.
Preparation of Similarity Matrix.
Conversion of Similarity Matrix into graph/network to apply the PageRank Algorithm. 
Applying the PageRank Algorithm.
Extracting summary using top N sentences based on their rankings.




