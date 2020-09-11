# Term-Deposit-Subscription
### Goal:
The data is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict if the client will subscribe a term deposit (variable y).
### Data Set Information:
Dataset from : http://archive.ics.uci.edu/ml/datasets/Bank+Marketing.
The data is related with direct marketing campaigns of a Portuguese banking institution. The marketing campaigns were based on phone calls. Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.
### Attributes:
- Age (numeric)
- Job : type of job (categorical: 'admin.', 'blue-collar', 'entrepreneur', 'housemaid', 'management', 'retired', 'self-employed', 'services', 'student', 'technician', 'unemployed', 'unknown')
- Marital : marital status (categorical: 'divorced', 'married', 'single', 'unknown' ; note: 'divorced' means divorced or widowed).
- Education (categorical: 'basic.4y', 'basic.6y', 'basic.9y', 'high.school', 'illiterate', 'professional.course', 'university.degree', 'unknown')
- Default: has credit in default? (categorical: 'no', 'yes', 'unknown')
- Housing: has housing loan? (categorical: 'no', 'yes', 'unknown')
- Loan: has personal loan? (categorical: 'no', 'yes', 'unknown')
- Contact: contact communication type (categorical:'cellular','telephone')
- Month: last contact month of year (categorical: 'jan', 'feb', 'mar',…, 'nov', 'dec')
- Dayofweek: last contact day of the week (categorical:'mon','tue','wed','thu','fri')
- Duration: last contact duration, in seconds (numeric). Importantnote: this attribute highly affects the output target (e.g., ifduration=0 then y='no'). Yet, the duration is not known before a callis performed. Also, after the end of the call y is obviously known.Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
- Campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
- Pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
- Previous: number of contacts performed before this campaign and for this client (numeric)
- Poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
- Emp.var.rate: employment variation rate - quarterly indicator(numeric)
- Cons.price.idx: consumer price index - monthly indicator (numeric)
- Cons.conf.idx: consumer confidence index - monthly indicator(numeric)
- Euribor3m: euribor 3 month rate - daily indicator (numeric)
- Nr.employed: number of employees - quarterly indicator (numeric)
- y - has the client subscribed a term deposit? (binary: 'yes', 'no')
### Data Cleaning:
#### Categorical Variables:
Using the get dummies method of pandas library, the attributes containing categorical variables were converted into one hot encoded features. I opted to not drop the unknown category for any attribute because in my opinion it may be useful in our model development and results.
#### Numerical Attributes:
Some of the numerical attribuites like age and campaign were cut off into different categorical segments in the form of a new column. Then one hot encoding was applied to these new categorical columns.
Numerical attributes pdays and campaign were directly mapped into new columns.
#### Factorial Analysis:
Five social and economic attributes employment variation rate, consumer price index, consumer confidence index, euribor three month rate and number of employees showed promising correlation with each other. Hence, I performed factorial analysis on them, converting them into a single attribute.
### Exploratory Data Analysis:
#### Age:
Majority of the people in the data set provided are middle aged people showing the imbalance in the data set. We can also see that the previous campaigns were also successful on mostly middle aged people.
#### Job:
The most common jobs in the data set provided are either administrative jobs or blue collar jobs. People who previously made subscriptions mostly belong to administrative, blue collar jobs or are technicians.
#### Marital Status:
The vast majority of perople in the dataset are married. While number of people who subscribed before were mostly married or single.
#### Education:
All education categories were almost equal in number with people having university degree being dominan both in number and in previous subscriptions.
#### Deafult Credit:
Most people have no default credit and a large number of them subscribed previously.
#### Housing:
People who own housing or not are almost equal in number in the data set as well as also their number of previous subscriptions.
#### Loan Status:
Mostly people who subscribd before are the ones who did not take loan.
#### Number of times a person was contacted during this campaign:
The people who were contacted fewer times during this campaign have a good amount of people who subscribed previously.
#### Other Contacts:
It also looks like the previous campaigns were more successful for people who were not contacted before the campaign.
### Model Development:
The usual drill was followed with data normalization and train-test split. However, a thing we noticed while doing exploratory data analysis was that the data set is highly imbalanced in favour of no or 0.
So, to counter this I did upsampling on the training set. The code for upsampling was obtained from https://github.com/gogundur and I am really grateful to her for the neat and clean code for upsampling.
####Logistic Regression:
Following results were obtained for logistic regression.
#### Support Vector Machines Classifier:
Following results were obtained for support vector machines classifier.
#### Random Forest Classification:
Following were the results obtained for random forest classification.
#### K Nearest Neighbors:
Following were the results obtained for KNN classification.
#### Decision trees:
Following were the results obtained for decision trees classification.
### Summary:
The best results were obtained from random forest classifier. But if we look at the confusion matrices, we observe that overall, decision trees performed better for both labels 1 and 0 overall. But still the performance of random forest classifier looks promising enough to be accepted as the final model. You can further modify the model to further improve its accuracy on your own.


