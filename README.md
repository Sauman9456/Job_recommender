# Job_recommender

## **EDA:** 


1.   From Countplot we can see that the Given dataset is balanced. So we will use Accuracy as our evaluation matrix
2.   mentee_major has closed to 1800 missing values,mentor_major has closed to 1200 missing values, mentee_help_topics has closed to 16000 missing values, mentor_help_topics has closed to 1400 missing values
3.   Top 3 skills selected by mentees in college are: 1) Business administration 2) Computer networks and cybersecurity 3) Psychology
4.   Top 3 skills selected by mentors in college are: 1) Business administration 2) Computer networks and cybersecurity 3) Information system management
5.   Top 3 topics in which mentees are seeking help: 1) Career planning 2)  Career / industry trends 3) General networking
6.   Top 3 topics in which mentors are willing to help: 1) Leadership skills 2)  Career / industry trends 3) Management
7.   Top 3 domains in which mentees are looking to build
 expertise: 1) computer - it services 2)  Cybersecurity 3) Business services
8.   Top 3 domain in which mentors has expertise: 1) computer - it services 2)  government / public admin 3) Business services

## **Method_1: Using Word Mover’s Distance**
In this method we have performed the following steps:


1.   Pre_processing: Removing Stop words, Square brackets, single quotes, Converting into lowercase
2.   Creating Vocabulary from the given dataset and adding it to Word2vec models
3.   Feature Engineering: Getting the similarity Score between mentee & mentor using Word Mover’s Distance
4.   Handling the Infinity values
5.   Multicollinearity check
6.   Model selection via cross-validation: Best performing models using this method are
            
            XGBClassifier  -> CV_score = 0.667731
               
            LGBMClassifier -> CV_score = 0.647682




## **Method 2: Using pre_trained models(Hugging Face)**
In this method we have performed the following steps:

1.   Pre_processing: Removing Stop words, Square brackets, single quotes, Converting into lowercase
2.   Loading the pre_trained model
3.   Feature Engineering: Embedding & Cosine similarity
4.   Handling the Infinity values
5.   Multicollinearity check
6.   Model selection via cross-validation: Best performing models using this method are
            
            XGBClassifier          -> CV_score = 0.687615
            
            LGBMClassifier         -> CV_score = 0.701751
            
            RandomForestClassifier -> CV_score = 0.694693

**Note: Method 2 gives better performance. So we will use this method for Hyperparameter Tuning**

7.   Hyperparameter Tuning: After this step
![alt text](https://github.com/Sauman9456/peoplegrove/blob/main/image/n_esti.png)
            
            XGBClassifier          -> score = 0.7194
            
            LGBMClassifier         -> score = 0.7190
8.   Learning curve for Overfitting and Underfitting
![alt text](https://github.com/Sauman9456/peoplegrove/blob/main/image/Learning%20curve.png)
            
            1.   As training set size increases testing accuracy increases. Therefore adding more data will increase the performance
            
            2.   Training accuracy is high, so our model has a low bias
            
            3.   Gap between the two curves indicates variance. Generally, the more narrow the gap, the lower the variance. 
            The opposite is also true: the wider the gap, the greater the variance. here we have a high variance
            
            4.  This high variance problem can be solved by adding more data, as we can see that, in the graph slope of 
            the test accuracy is more than train accuracy
            
            5.  Generally in low bias and high variance,  XGboost perform well


![alt text](https://github.com/Sauman9456/peoplegrove/blob/main/image/Confusion%20matrix.png)
