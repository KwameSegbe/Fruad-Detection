# Fruad-Detection
# Project Report
Francis Kwame Segbe
Fraud Detection

# Introduction
To analyze the new account application data and answer questions from the Vice President,
We decided to select two out of several machine learning algorithm methods: exploratory
data analysis (EDA) and principal component analysis (PCA). For test completeness sake we
added logistic regression with SMOTE balancing.
Through exploratory data Analysis, we were able to visually explore the data, identify any
outliers, and also understand the relationships between features. These visualizations
helped us answer many of the descriptive questions the Vice President has asked.
Principal component analysis is an unsupervised machine learning method that reduces the
dimensionality of the data while retaining most of the variation. We did this to identify the
most important features and group similar applicants together. PCA answers questions
about clustering, predicting fraud, and potential weaknesses.

# Exploratory Data Analysis
First, we loaded the variant1.csv dataset and examined the features. The data contains
simulated new account application events with 21 features like customer_age, income,
credit_risk_score, etc. There is also a column indicating if the event is fraudulent or not this
column is the fraud_bool column.
To explore the data, we had to create visualizations like histograms, correlation plots, and
scatterplots. The fraud rate is very low - only 1.1% of events are fraudulent. Most of the
applicants were in their 20s-40s, with incomes around $40k-60k. Fraudulent events seem
randomly mixed with normal events.
Below is we have age distribution and income distribution of applicants.
In [61]:

As mentioned above, the heatmap here shows that, fraud seams to have assimilated well
with the applicants and is very different and can be indistinguishable from the normal set.
The only values that seem to have any significant correlation are the credit _risk _score and
proposed_credit_limit.

This tells us that the firm has a diverse applicant pool with no obvious outlier clusters. It may
be difficult to accurately predict fraud since fraudulent applications appear similar to
normal ones. Below are some of the visualizations performed by the team. While performing
the visualization and data cleaning, we realized some of the features were non-numeric
features so we had to take them out, further, we also identified that some of the features had
more than 25% missing values by referencing the guide book, any negative 1(-1) one digit
represented an empty cell. By this, we took out some features as well further reducing the
features we had to work with.
# Principal Component Analysis
Next, we applied PCA to the dataset. The main purpose was dimensionality reduction. We
wanted to reduce the dimensions of the data so that we would get just the most important
features, This process condenses the 21 features down to 4 principal components
explaining most of the variance.
The first component correlates with credit history features. The second relates to
income/assets. The third includes applicant_age and housing variables. The fourth
component highlights debt factors.
Projecting the data onto the first two components shows one dense cluster of normal
applicants, with fraudulent applicants scattered randomly. This fits well with the Exploratory
data analysis findings - fraudulent events blend into the normal population.

# LOGISTIC REGRESSION
We did a SMOTE on our cleaned dataset and after the SMOTE to get get a much-balanced
dataset we run a logistic regression model on it. The logistic regression model produced the
following results. It achieved 0.627 accuracy on the test set. The AUC was 0.672, with
precision, recall, and F1 scores around 0.63 for both classes. The confusion matrix showed
a balance of false positives and negatives.
The results from our model reflect the difficulty in identifying dispersed fraud within normal events. 
Doing continued model tuning and new data may improve accuracy. However, inherent data challenges will constrain
performance. This ultimately aligns with our two previous claims from PCA and EDA
performed. Below are the results from our predictive model.

# Answers to VP's Questions
1. What does the method and data tell you about the firm's new account
applicants? Explain. [Please note: The Vice President already knows that applicant
fraud is somewhat rare.]

Answer: The exploratory data analysis and PCA modeling revealed that the firm's
applicant population is quite diverse and heterogeneous, spanning a wide range of
ages, income levels, credit profiles, etc. Within this broad applicant pool, fraudulent
events are relatively rare, occurring at a rate of just 0.17% based on the fraud indicator
in the dataset. Additionally, the analysis indicates that the fraudulent applications
are not concentrated in specific segments or clustered separately. Instead, fraud
occurs randomly across various applicant profiles, essentially disguising itself
among the larger normal applicant population.
The PCA specifically shows that both normal and fraudulent applicants intermix
within one dense central cluster, rather than separating into distinct groups.
This dispersed nature of fraud makes detection more challenging. Fraudsters hide
their activities amongst innocuous everyday applicants exhibiting ordinary,
acceptable characteristics. Sophisticated schemes effectively mimic legitimate
behavior.

2. What features in the data seem to matter more in your analysis and method?
Answer: Credit history, income, age, and debt factors seem most important.

3. There are fraudulent applicant events flagged in the data. Is there anything
unique about those events?
Answer: It doesn’t look like there is some abnormality with the fraudulent events that
make them unique - they look very similar to normal applicants.

4. Are the fraud applicant events outliers -or- do they seem to blend in with or look
the same as the rest of the firm's legitimate applicants?
Answer: Fraudulent events assimilated into the normal applicant population. As we
can see in the PCA graph and also in our heatmaps created.

5. Does the firm have multiple clusters of applicants? If yes, explain how they are
unique. If no, explain why not.
Answer: We could notice one major cluster of applicants, with no clear sub-clusters.
From our PCA analysis, there appears to be only one main cluster of applicants, with
no clear segmentation into multiple distinct clusters. The PCA scatterplot shows the
majority of applicants concentrated into one dense cluster, with no obvious separate
groupings. This suggests the applicant population is quite heterogeneous without
strong inherent subgroups.

6. Is there a chance that the firm might potentially miss applicant events that might
actually be fraudulent? Explain your answer.
Answer: Yes, There is high probability the firm could miss some fraudulent events due
to the way these activities blend with normal applicants. This is because according to the
analysis, the fraudulent events are dispersed and mixed within the large cluster of normal
applicants. The fraudulent events do not diverge into their own cluster but rather mix into
the normal population across various profiles. This makes accurate identification difficult.

7. Within the data, are their certain applicant events that will never be considered
fraudulent? If yes, what are the common data features of those applicants? If no,
why?
Answer: No specific group of applicants can be considered non-fraudulent. This is
primarily because: Fraudulent events are dispersed across various applicant profiles
rather than concentrated in specific segments.
Even applicants that may appear low risk based on certain attributes still exhibit
some fraudulent activity. For example, older applicants with high incomes and
excellent credit do have some fraud cases.
The features available in the data may not fully encapsulate all the drivers of fraud
risk. There may be other attributes that better predict propensity for fraud that are not
captured. Sophisticated fraudsters can manufacture identities and profiles that
appear legitimate across metrics in the data. This enables them to hide among
applicants that look benign.

8. Do you think the firm could predict future fraudulent events with this data
set? Yes or No? Provide a short explanation.
Answer: The data could predict fraud with moderate accuracy. Fraud is disguised,
limiting predictive power.

9. What metrics did you use to evaluate the accuracy of the methods you chose?
Please list.
Answer: Accuracy metrics like ROC-AUC, precision, recall, and F1-score.
10. At what specific step (or steps) within the fraud kill cycle could your method be
utilized by the firm to help stop potential fraud amongst applicants?
Answer: This could help during account screening to flag risky applicants for further
review.

11. How could your analysis be used by the firm to help pro-actively or re-actively
detect fraud?
Answer: Analysis highlights important factors to monitor. Model scores could rank
applicants by risk.

12. What are the potential weaknesses in your chosen methods?
Answer: Limited fraud cases and disguised data make accurate prediction difficult.

# Conclusion
In summary, Exploratory Data Analysis and Principal component analysis give us insight into
the applicant population and fraud characteristics of our dataset. The analysis indicates
predicting fraud will be a very challenging and tedious task but still possible if we implement
proper monitoring of key risk factors.
# Referrence
https://cris.maastrichtuniversity.nl/ws/files/129458552/c7833.pdf
https://builtin.com/data-science/step-step-explanation-principal-component-analysis
https://www.analyticsvidhya.com/blog/2016/03/pca-practical-guide-principalcomponent-
analysis-python/
https://towardsdatascience.com/exploratory-data-analysis-8fc1cb20fd15
https://www.acfe.com/
