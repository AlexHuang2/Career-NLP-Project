# Text Classification Model for Industry

A high level overview of `classification_model_industry.ipynb` is that it's a model that takes in a WOKEN user's typeform answers (that are relevant to industry), and tells them what industry they are best suited for. How is this accomplished?

## Collecting and Preprocessing the Training Data

The training data was collected from LinkedIn using a web scraper. Each LinkedIn profile that was scraped becomes data in the form of a text "document", which gets labeled with its corresponding industry.

## Collecting and Preprocessing the Test Data

The test data is collected from the typeform assessment that is administered to WOKEN customers. It is a text document of their answers to the relevant questions on the assessment, and Rachel has assigned to them the correct labels.

## Model Selection and Training

To encode the aforementioned text documents in vector form, we used a TF-IDF vectorized representation of each (tokenized) word in the text document. The TF-IDF of a word is a score that is proportional to the frequency of the word in a document, but inversely proportional to the number of documents the word is in. For example, the word "the" shows up many, many times in each document, but also appears in all documents. Therefore, its TF-IDF score is 0, as it should be because its existence in a document serves little value in classifying that document into a category. On the other hand, the word "coding" will show up frequently in documents that are labeled "technology", but not in other industries. As such, it will have a high TF-IDF score.

For the classification portion of the model, we used logistic regression (Further work would have involved tuning the hyperparameters of the LogisticRegression function so that it maximized the out-of-sample accuracy).

For the purposes of this particular application, accuracy on the test (typeform) data is defined as 1 of the 3 industries determined by the model being the correct labeled one. This makes sense for this particular application because we are trying to be open ended as much as we are trying to be correct. 
