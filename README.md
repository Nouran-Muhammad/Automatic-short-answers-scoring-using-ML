# Automatic-short-answers-scoring-using-ML

Automatic scoring for educational systems has attracted much attention during the past years as it saves time. Many approaches have been taken to ensure accurate and fair resutls in automatic scoring of student's answers.

## Dataset used: Texas2011 
- 85 unique questions with model answer
- Total of 3646 rows 
- Columns: Question, Model Answer, Answer, Score


## My Approach:
My approach uses the power of context embedding by transformers - SentenceBert - and the simplicity of machine learning models - RandomForest Regressor - to create a solution for the problem.

The pipline expects the following input:
- Question, Model Answer, Answer
or
- Question, Context about the exam/interview, Answer

![image](https://github.com/Nouran-Muhammad/Automatic-short-answers-scoring-using-ML/assets/61350907/19075470-45cd-4401-85c1-63b53ab1d553)

### 1- Pre-processing
##### In case of model answers given: 
- Convert to lowercase
- Remove non alphanumeric characters

##### In case of context given: 
- Convert to lowercase
- Remove non alphanumeric characters
- Remove stop words

### 2- Feature Extraction
##### In case of model answers given: 
    1- Sentence embeddings for questions, model answers and answers using SentenceBert
    2- Cosine similarity between model answer and answer embedding vectors
    3- Calculate the overlap of words between model answer and answer (number of common words)
    4- PCA is done on the embeddings to reduce the dimensions to prevent overfitting with keeping dimensions of highest variance


#### In case of context given: 
    1- Sentence embeddings for questions and answers using SentenceBert
    2- Extract TF_IDF features for context
    3- Use TF_IDF features extracted from context and transform the answers
    4- PCA is done on the embeddings to reduce the dimensions to prevent overfitting with keeping dimensions of highest variance
    
    
## Sample Results
Train MAE:  0.21, Test MAE:  0.49

![image](https://github.com/Nouran-Muhammad/Automatic-short-answers-scoring-using-ML/assets/61350907/32228d3b-1697-4d62-9240-2d213d287e05)
