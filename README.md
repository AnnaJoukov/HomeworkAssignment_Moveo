# HomeworkAssignment_Moveo
Homework Assignment: Grouping Patent Texts for Mobile Communication Analysis
Python version 3.12
----------------------------------------------------------------------------
Task 1:Extracting text from patents
The function extract_patent_claims retrieves patent claims from a given URL by fetching the HTML content, parsing it with BeautifulSoup, and extracting text from specific HTML elements containing the claims.
A list of patent URLs is defined, and the claims are extracted from each URL using the extract_patent_claims function, then combined into a single list.
The preprocess_claims function processes the extracted claims by converting text to lowercase, removing non-alphabetic characters, tokenizing the text, lemmatizing the words, and removing stopwords.
All the extracted claims are processed, resulting in a list of preprocessed text.
I took the documentation for this part of the code from the following website: https://www.crummy.com/software/BeautifulSoup/bs4/doc/.

Task 2: Grouping claims by topic
I used three different methods for grouping paragraphs:

BERT Model: A pre-trained language model used to generate contextual embeddings.
LDA Model: A clustering algorithm that groups paragraphs by identifying topics within the text based on word distributions.
K-Means Clustering: A clustering algorithm that groups paragraphs into clusters by minimizing the variance within each cluster based on the paragraph embeddings or feature vectors.
--If I had more time I would also try to use GPT model https://medium.com/@sumit.tripathi/learning-how-to-build-your-own-gpt-on-python-173258a0eb33--

Due to the fact that my computer doesn't have a GPU, I had to install PyTorch through Anaconda (via the Anaconda Prompt).
The loading time for running all the methods together in one notebook was too long, which caused my computer to crash, so I split each method into a separate notebook.Additionally, I chose to separate the notebooks to optimize the training process for each model. However, this increased the runtime of a single notebook that includes all three models.
I understand that it could have been executed in a more efficient and organized manner.

1. K-Means Clustering Method - importent notes:
  1.1 I used Elbow Method for calculating the optimal number of clusters.It identify the point where adding more clusters results in diminishing returns in 
  reducing within-cluster variance (See the graph).
  1.2 To evaluate the quality of the model, I used the Silhouette Score, which resulted in a score of 0.181.A Silhouette Score of 0.181 suggests that the clusters 
  formed by the model are not well-separated and 
  may overlap significantly.I attempted to improve the results by adjusting the parameters(num_clusters) and enhancing the preprocessing steps, but these efforts 
  did not significantly improve the outcome.
K-means clustering is a popular data segmentation method due to its simplicity and speed. It's easy to implement and it can handls large datasets efficiently.
K-means clustering has several limitations that can impact its effectiveness, including its sensitivity to the choice of the number of clusters (k), the initial placement of centroids, and the shape and size of the clusters. Determining the optimal k can be challenging, and different initial conditions may lead to different outcomes. The algorithm also assumes that clusters are spherical with similar variances, making it less suitable for complex or irregular clusters.
The algorithm did generate topics (group titles) for each group, but it simply combined selected words into sentences that were not coherent. This issue might occur because the algorithm relies heavily on the most frequent or prominent words within each group, without considering their contextual relationships or the overall meaning.

2. LDA Method -  importent notes:
   2.1 To evaluate the quality of the model, I used the Coherence Score that evaluates the quality of topics by measuring the semantic similarity between the most 
   frequent words in each topic.A Coherence Score above 0.5-0.6 is considered reasonably good, while scores closer to 1.0 indicate very strong topic coherence.
   (https://www.baeldung.com/cs/topic-modeling-coherence-score)
   2.2 I tried adjusting the num_topics and passes parameters to achieve the best Coherence Score in order to make the model as accurate as possible. After various 
   attempts, I discovered that the optimal settings for this method are when num_topics = 10 and passes = 15. The range around these numbers typically results in a 
   Coherence Score between 0.6 and 0.7.
   Coherence Score for LDA: 0.639
   2.3 It is evident that the model is not very accurate, as it failed to generate claims for certain topics, such as Topic 9 and Topic 0. Additionally, the titles    are composed of key words that don't have much relevance or connection to each other.
One key advantage of LDA is that it is an unsupervised learning method, allowing it to automatically detect topics within your documents without needing predefined labels or categories. This can save time and effort while uncovering hidden patterns and insights.
One of the primary disadvantages of LDA is that it can sometimes generate ambiguous or incoherent topics, particularly when the data is noisy, sparse, or diverse.
The multiple iterations and optimization steps required to estimate topic distributions can demand significant resources and memory.

3. BERT Method - imporent notes:
   3.1 On my PC it took about 5 to 10 minutes to run the model.
   3.2 During the running process , errors will appear such as a "parameter name containing 'beta' will be internally changed to 'bias'...". As far as I 
   understand, this is talking about the update of the package and does not interfere with the running of the model.
   3.3  In this code, embeddings are powerful tools that allow you to represent complex text data in a meaningful, dense, and compact form.
   3.4 After the grouping process, the generated topics (group titles) were not clear or coherent, as seen in examples like "Group 1 Title: The gcp message  
       rotocol gcp. method according to claim comprises routing said." Despite the syntactical issues in the titles, this model still produced better overall 
       results compared to the other models.
   3.5 Another issue with the model is that it fails to recognize identical words consistently. For instance, in group 4, the title repeats the word "output" 
       multiple times, indicating a lack of understanding that these instances refer to the same concept.

BERT excels in understanding context through bidirectional attention, making it highly effective for complex NLP tasks. Its adaptability allows for fine-tuning across various applications, such as semantic search, resulting in high accuracy. However, BERT is computationally expensive, requiring substantial resources for training and inference. Additionally, it is limited by its reliance on specific attention patterns, which can lead to less optimal results.
The bidirectional attention mechanism in BERT allows the model to consider the context of a word by looking at both the words before and after it in a sentence. Unlike traditional models that process text in one direction (left-to-right or right-to-left), BERT processes the entire sentence at once, enabling it to capture the full context and understand the relationships between words more effectively.
https://www.yext.com/blog/bert-strengths-and-weaknesses-34eabc48587b
https://pareshmpatel.com/bert-or-chatgpt-the-pros-and-cons/

For creating an interactive application, BERT would be the best choice among the three models. BERT provides the most accurate and contextually relevant groupings and topic titles due to its deep understanding of language. Despite some challenges with syntactical coherence in the titles, BERT's results are generally more meaningful and reliable compared to LDA or K-Means. This will lead to a better user experience in my application, where users can see more relevant and contextually accurate groupings and topics.While it may be computationally intensive, the benefits in terms of accuracy and relevance make it the most suitable option for the application.








Task 3: Creating an interactive application
אפליקציה
Running on http://127.0.0.1:5000/
ברגע שמריצים על ג'ופיטר
BeautifulSoup השתמשתי בטול
מתוך הדוקימנציה הזו - https://www.crummy.com/software/BeautifulSoup/bs4/doc/
