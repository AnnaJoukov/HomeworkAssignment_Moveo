# HomeworkAssignment_Moveo
Homework Assignment: Grouping Patent Texts for Mobile Communication Analysis
Python version 3.12
----------------------------------------------------------------------------
Task 1:Extracting text from patents
The function extract_patent_claims retrieves patent claims from a given URL by fetching the HTML content, parsing it with BeautifulSoup, and extracting text from specific HTML elements containing the claims.
A list of patent URLs is defined, and the claims are extracted from each URL using the extract_patent_claims function, then combined into a single list.
The preprocess_claims function processes the extracted claims by converting text to lowercase, removing non-alphabetic characters, tokenizing the text, lemmatizing the words, and removing stopwords.
Finally, all the extracted claims are processed, resulting in a list of preprocessed text.
I took the documentation for this part of the code from the following website: https://www.crummy.com/software/BeautifulSoup/bs4/doc/.
-----------------------------------------------------------------------------
Task 2: Grouping claims by topic
I used three different methods for grouping paragraphs:

BERT Model: A pre-trained language model used to generate contextual embeddings.
LDA Model: A clustering algorithm that groups paragraphs by identifying topics within the text based on word distributions.
K-Means Clustering: A clustering algorithm that groups paragraphs into clusters by minimizing the variance within each cluster based on the paragraph embeddings or feature vectors.
--If I had more time I would also try to use GPT model https://medium.com/@sumit.tripathi/learning-how-to-build-your-own-gpt-on-python-173258a0eb33--

Due to the fact that my computer doesn't have a GPU, I had to install PyTorch through Anaconda (via the Anaconda Prompt).
The loading time for running all the methods together in one notebook was too long, which caused my computer to crash, so I split each method into a separate notebook. 
I understand that it could have been executed in a more efficient and organized manner.

1. K-Means Clustering - import notes:
  1.1 I used Elbow Method for calculating the optimal number of clusters.It identify the point where adding more clusters results in diminishing returns in reducing within-cluster variance (See the graph).
  1.2 To evaluate the quality of the model, I used the Silhouette Score, which resulted in a score of 0.181.A Silhouette Score of 0.181 suggests that the clusters formed by the model are not well-separated and 
  may overlap significantly.I attempted to improve the results by adjusting the parameters(num_clusters) and enhancing the preprocessing steps, but these efforts did not significantly improve the outcome.
K-means clustering has several limitations that can impact its effectiveness, including its sensitivity to the choice of the number of clusters (k), the initial placement of centroids, and the shape and size of the clusters. Determining the optimal k can be challenging, and different initial conditions may lead to different outcomes. The algorithm also assumes that clusters are spherical with similar variances, making it less suitable for complex or irregular clusters.










Task 3: Creating an interactive application
אפליקציה
Running on http://127.0.0.1:5000/
ברגע שמריצים על ג'ופיטר
BeautifulSoup השתמשתי בטול
מתוך הדוקימנציה הזו - https://www.crummy.com/software/BeautifulSoup/bs4/doc/
