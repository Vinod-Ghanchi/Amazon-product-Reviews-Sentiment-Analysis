# sentimentanalyis_1
		
 ![image](https://user-images.githubusercontent.com/80514865/189485510-8773d14d-2f14-4a48-917e-505bca6f1d8e.png)

Steps involved in completing this task:
1.	Scrapping the data: We scrapped the data from amazon.com using beautiful soup in python. In this step we created different function for extracting the single page data using data asin number(unique identification number) of products. Using this data-asin number, we were able to extract all the reviews of a particular product and also similar products from all the pages available. In this manner we extracted all the reviews of all the products from all the pages and stored them into a form of list. We converted this list into dataframe using pandas and then converted it to excel and csv.

2.	Preprocessing the data: The data we extracted was not clean data. We need to clean the data first before we could apply any classification techniques on it. For this used “spacy” module. We checked for all the null values, and replaced it with empty string “”. Firstly we converted all the reviews from the reviews column to lowercase and stored it into a new column new_reviews. Next, we remove punctuations, then emojis, pictographs and stopwords like a, the, etc and many more. We then lemmatized the words into their root words. This is the cleaned dataset on which we can work on.


3.	Labelling the reviews dataset: For this step we imported modules “vader” and “nltk”. Using vader module, we calculated the polarity scores of each rows in reviews column. We got the values of positive, negative, neutral and compound. Depending on the compound values, we can label the reviews as having positive and negative polarity. For the compound values more than -0.5, we treated them as positive and labelled it as 0 and for the values less than -0.5, we treated them as negative review and labelled it as 1.

4.	Naïve Bayes model: Using sklearn module, we applied naïve bayes classifier on our labelled data. Firstly we splitted the dataset into train and test set as 70% and 30%. Using the count vectorizer function, we tokenized the document into a matrix. We have also entered a user defined list to see the result of this function and it showed us as below 
 ![image](https://user-images.githubusercontent.com/80514865/189485521-af58922b-0cab-4611-b07d-8da3893724ed.png)


As shown, it tokenize each word in the list and shows us the frequency. We applied the same to our train and test dataset.
For this we used multinomial naïve bayes classifier model. After fitting the vector to the model, we got the following confusion matrix. 
 ![image](https://user-images.githubusercontent.com/80514865/189485530-7c8d34dc-fcf2-4f84-be2c-ecab57432942.png)

The accuracy score using this model was 92.33%. <br/>
Using the statsmodel module, we got the summary of the predicted result.<br/>  
![image](https://user-images.githubusercontent.com/80514865/189485544-5d8ce065-aae5-4726-9fc1-00c37263305d.png)

As we can see all the values are shown. 
Interpretation of OLS results
R squared value:
R2 is the coefficient of determination that tells us that how much percentage variation independent variable can be explained by independent variable. Here, 44.9 % variation in Y can be explained by X. The maximum possible value of R2 can be 1, means the larger the R2 value better the regression.
F-statistic value:
F test tells the goodness of fit of a regression. 
The null hypothesis under this is “all the regression coefficients are equal to zero”. Prob(F-statistics) depicts the probability of null hypothesis being true. 
The test is similar to the t-test or other tests we do for the hypothesis. The F – statistic is calculated as below –   
 
Inserting the values of R2, n and k, F = (0.449/1) / (0.551/1512) = 1232.1.
You can calculate the probability of F >1232.1 for 1 and 1512 df, which comes to approx. 0. As per the above results, probability is close to zero. This implies that overall the regressions is meaningful.

The remaining terms are not often used. Terms like Skewness and Kurtosis tells about the distribution of data. Skewness and kurtosis for the normal distribution are 0 and 3 respectively. Jarque-Bera test is used for checking whether an error has normal distribution or not.

Using pickle module, we deployed our model or project in python to a .pkl format file.
![image](https://user-images.githubusercontent.com/80514865/189485566-5dfe730e-cb08-438b-9541-a39a6bf33437.png)
![image](https://user-images.githubusercontent.com/80514865/189485571-e0660358-8dbd-4b0b-a08f-66e90e13b769.png)


 
 
As we can see it showed us the expected result i.e. negative sentiment. 
 ![image](https://user-images.githubusercontent.com/80514865/189485573-630388a2-b153-4808-863e-92454216e401.png)
![image](https://user-images.githubusercontent.com/80514865/189485580-ad4d30c5-9ce0-4d53-9c99-29c0144a3b31.png)

 
As we can see it showed us the expected result i.e. positive sentiment. 


5.	SVM model: The second model that we used was svm model. All the function and the code till the model selection is the same as the naïve bayes model code. Using sklearn we selected svm linear model. The accuracy using this model came out to be 96.38%. 
After fitting the vector to the model, we got the following confusion matrix. <br/>
 ![image](https://user-images.githubusercontent.com/80514865/189485591-9eb2d1b1-19f0-4fb0-bd1c-4a408710ca06.png)






The OLS results are as below: <br/>
 ![image](https://user-images.githubusercontent.com/80514865/189485620-17f865df-181a-4ef6-8ed8-d11aed4052a6.png)

Interpretation of OLS results:
R squared value: Here, 74.2 % variation in Y can be explained by X. The maximum possible value of R2 can be 1, means the larger the R2 value better the regression.

F-Statistic value: Inserting the values of R2, n and k, F = (0.742/1) / (0.258/2268) = 6522.7.
You can calculate the probability of F >6522.7 for 1 and 2268 df, which comes to approx. 0. As per the above results, probability is close to zero. This implies that overall the regressions is meaningful.

As above step, we deployed this model too using pickle module.
![image](https://user-images.githubusercontent.com/80514865/189485626-3d5161ec-2877-4d4f-aed5-ea5d8df46371.png)
![image](https://user-images.githubusercontent.com/80514865/189485632-bdcfa63e-db4d-41c2-8bef-1b685316012e.png)

 
 
As we can see it showed us the expected result i.e. negative sentiment. 
![image](https://user-images.githubusercontent.com/80514865/189485637-c3f37d0a-2b3c-4ebb-a6aa-ab567f54e647.png)
![image](https://user-images.githubusercontent.com/80514865/189485640-75254d52-a4e2-4cdf-8555-d0523414f56e.png)

 
 
As we can see it showed us the expected result i.e. positive sentiment. 

6.	Decision tree model: The last model that we used was decision tree model. All the function and the code till the model selection is the same as the naïve bayes model code. Using sklearn we selected decision tree model and set the criterion to entropy. The accuracy using this model came out to be 95.01%. 
The confusion matrix of using this model is as below:<br/>
 ![image](https://user-images.githubusercontent.com/80514865/189485645-ca63f582-bed5-4300-9d42-0b341a3da50a.png)

The OLS results are as below:<br/>
 ![image](https://user-images.githubusercontent.com/80514865/189485649-7429ae33-edca-434e-baa4-045ea6c033f1.png)

Interpretation of OLS results:
R squared value: Here, 66.5 % variation in Y can be explained by X. The maximum possible value of R2 can be 1, means the larger the R2 value better the regression.

F-Statistic value: Inserting the values of R2, n and k, F = (0.665/1) / (0.335/2268) = 4502.1.
You can calculate the probability of F >4502.1 for 1 and 2268 df, which comes to approx. 0. As per the above results, probability is close to zero. This implies that overall the regressions is meaningful.

As above step, we deployed this model too using pickle module.
![image](https://user-images.githubusercontent.com/80514865/189485653-65caeec3-ad3f-4b7f-be9a-0624f906b428.png)
![image](https://user-images.githubusercontent.com/80514865/189485662-08302a60-83bb-4380-8a33-da9ba6b96e1b.png)

 
As we can see it showed us the expected result i.e. negative sentiment. 

 ![image](https://user-images.githubusercontent.com/80514865/189485664-ebefb89a-2568-435f-9cd5-4d69e9a12582.png)
![image](https://user-images.githubusercontent.com/80514865/189485667-70c600c4-517a-41ad-bec4-abf4be51d1b5.png)


 
As we can see it showed us the expected result i.e. positive sentiment. 






Comparison of the three models:<br/>
 ![image](https://user-images.githubusercontent.com/80514865/189485672-b9611c2c-e1e2-47b6-8370-f5efb8af7609.png)
![image](https://user-images.githubusercontent.com/80514865/189485679-ef0a7c55-3ed8-4fdd-94f9-391353d66ebc.png)


 

Conclusion: As we can see from both the graphs, svm has the highest r squared value and accuracy, so we conclude that in our task of sentiment analysis, SVM model is of best use.

*We have added comments in all the code files so that it would be easy to interpret*
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
Steps to execute :
If you want to change the product while scrapping enter the item name in search_query on line 8 in the scrapping folder amazonscrape.ipynb file
Convert the data to csv in the same directory.
Enter the address of the scrapped dataset into read_csv section in pre processing and after pre processing save the pre processed file in the same directory.
Load the pre processed dataset in the labelling file and save it in the same directory .
Models: Load your labelled dataset in all the model files. 

![image](https://user-images.githubusercontent.com/82643868/189821541-c960481c-3aea-47da-a046-725be274ea15.png)
![image](https://user-images.githubusercontent.com/82643868/189821755-42d55edc-f3d3-4fad-9b94-612dd692348d.png)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
