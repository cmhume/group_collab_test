# eCommerce Business Trends


## Presentation


### Group Members


Elaine Ng - Technology (X role), Branches: [Repo Branch](https://github.com/cmhume/eCommerce_Business_Trends/tree/Elaine), [technology.md](https://github.com/cmhume/eCommerce_Business_Trends/tree/technology.md)


Luz Maria Cabral - Database (Circle role), Branches: [Repo Branch](https://github.com/cmhume/eCommerce_Business_Trends/tree/Luz), [Database](https://github.com/cmhume/eCommerce_Business_Trends/tree/Database)


Manupriya Sharma - Machine Learning Model (Triangle role), Branches: [Repo Branch](https://github.com/cmhume/eCommerce_Business_Trends/tree/Manupriya), [Machine_Learning](https://github.com/cmhume/eCommerce_Business_Trends/tree/Machine_Learning)


Corinne Hume - GitHub (Square role), Branches: [Repo Branch](https://github.com/cmhume/eCommerce_Business_Trends/tree/Corinne), [readme_wk1](https://github.com/cmhume/eCommerce_Business_Trends/tree/readme_wk1)


### Project 


**Selected Topic:** Brazilian eCommerce Business Trends


In this project, we will analyze customer orders placed between 2016-2018 from sellers on the Brazilian eCommerce platform [Olist Store](https://olist.com/).  From this data, we will first determine the number of customers by geographic region (looking at zip code prefix, city, and state), most popular products, number of repeat customers and purchases, and total purchases by date. After data cleaning and initial analysis, we will use machine learning to make predictions on customer behavior, providing sellers on Olist the opportunity to increase sales and their customer base.


**Why we selected our topic:** 

We selected this topic because of the analysis options available from eCommerce data, with information available on customers, sellers, products and geographic regions.  We would like to know if consumer behavior differs between customer's geographic location and if future purchases could be predicted using geolocation data. We would also like to know what products are likely to be purchased depending on the time of year.  Our ultimate goal is to predict consumer behavior from this dataset using machine learning.

**Description of our source of data:**

We chose the [Brazilian-eCommerce](https://www.kaggle.com/olistbr/brazilian-ecommerce) dataset from Kaggle for our analysis.  This dataset contains approximately 100,000 customer orders, along with corresponding files on product information and English translations of product categories originally in Portuguese. Seller names in this dataset were anonymized and replaced with Game of Thrones House names.  Six files from the original Kaggle dataset were chosen for further analysis: geolocation dataset, olist_customers_dataset, olist_product_dataset, order_item_dataset, olist_orders_dataset, and product_category_name_translation. 

*_Data Source: https://www.kaggle.com/olistbr/brazilian-ecommerce_*

**Questions we hope to answer with our data:**

With this data, we hope to answer...
- What is the ordering behavior for consumers in each geographical region?
- What type of products would a company expect to buy more of depending on the season?
- Analyse reviews and develop predictive model based on the given parameters. 


### Communication Protocol


* We will coordinate and communicate through Slack and Zoom. Our team will meet on Zoom every Monday, Wednesday and Thursday. 


#### Planning Meeting:


* Every Monday we will meet to plan the deliverables and responsibilities for the entire week. Everyone will work on their branch or feature branch on Github.


- **Google Drive:** To add websites with data, brainstorm topics to choose from, and share our files for the project


#### Debugging Session:


* Every Wednesday we will discuss challenges and try to debug issues together.


#### Merging work to main branch


* We will post on slack before merging to the main branch and after creating new branches.


* On Sundays at 7pm, we will check in on Slack to review our GitHub page before turning in the assignment on Canvas.  


## Machine Learning

We plan on trying a variety of machine learning models on our database and choosing the best performing model for our final analysis. We choose the following classification models to analyse our data:
- Logistic Regresssion
- K-NN model
- SVM model: Linear
- Kernel SVM: Non Linear
- Decision Tree
- Ensemble: Randon Forest
- k-Fold Cross Validation
- Artification Neural Network


### Data Exploration


Jupyter notebook was used for initial data exploration as seen below:


[Data Exploration and Machine Learning Models](https://github.com/cmhume/eCommerce_Business_Trends/blob/c9e1c5a6ad08d4dadfdfad7846ac6b0e262dcc3e/Machine_Learning/ecommerce_business_trend.ipynb)


![Screenshot (376)](https://user-images.githubusercontent.com/78699521/127748015-09d78f09-7d16-40d4-b3db-c41e5c681123.png)


### Mock-up Machine Learning Model


link to mock-up machine learning model


## Database

To begin with this analysis we reviwed the different information that was provided by the six datasets we chose to work with. Using the Quick DAtabse Diagrams (Quick DBD) we were able to draw out our datasets using the Entity Realtionship Diagrams (ERD) and find the relation between all of them and mapped how we would merge our data to achieve the results we had set for ourselves. 

![FP_ERD3](https://user-images.githubusercontent.com/78699521/127382944-ff63d2b2-e908-4af9-b303-53484415c826.png)

### Cleaning files and creating tables

To clean and merge datasets we used a combination of jupyter notebook/pandas and PostgresSQL/pgAdmin interface. As we tried to upload the datasets to pgAdmin we noticed they needed some light cleaning and removing of duplicate information. It was easier to do the cleaning in Jupyter Notebook, and such was used to clean geolocation dataset, olist_product_dataset, order_item_dataset, and olist_orders_dataset; this shrank our datasets with very few data lines still leaving us with thousands of entries to work with. After cleaning they were easily uploaded to postgres with new titles; geolocation_revies.csv, order_item_revised, order_list_revised, and product revised and we were able to merge some datasets to better fit our analysis. 

[Jupyter Notebook](https://github.com/cmhume/eCommerce_Business_Trends/blob/Database/Geolocation_revised.ipynb)


![Screenshot (374)](https://user-images.githubusercontent.com/78699521/127747712-3ffa02c2-8c5d-47d6-b77b-02c6661d90ab.png)


In regards to product analysis and sales we decided it would be optimal to merge product_revised with product_category_name_translation, order_item_revised, order_list_revised, and the olist_customers_dataset. Combining all these datasets with common information via inner joins were able to provide all we need in one dataset, who's ordering, what they're ordering, and where it's going to. Price of item and freight is also included for company to review sales and costs. 


[Schema](https://github.com/cmhume/eCommerce_Business_Trends/blob/31305c1985f295618599131190d3154b92eb57e2/Wk__DB_orders.sql)


![Screenshot (372)](https://user-images.githubusercontent.com/78699521/127747331-f1bb587e-d59c-4443-b71a-6d2e2a3cdea7.png)

The combined dataset has over 99,000 entries, we understand we will need to take a sample of this to continue with our analysis since this dataset is mega. For the assignment this week we randomly selected a sample of 150 entries from this merged dataset and that's what is reviewed in our Machine Learning portion.   

[Product Sample Database](https://github.com/cmhume/eCommerce_Business_Trends/blob/31305c1985f295618599131190d3154b92eb57e2/product_sample.csv)

In addition, the geolocation_revised was merged with olist_customers_dataset to create order_locations.csv, in order to review purchasing behaviors across regions of the country. At this time our 3 main datasets we would be using is the purchase_data.csv, order_locations.csv and the order_item_revised.csv but this can change as our finding guide the research.

![Screenshot (371)](https://user-images.githubusercontent.com/78699521/127747399-f7e31ec6-1a79-48ed-a95d-301dfb8f8572.png)






![Screenshot (365)](https://user-images.githubusercontent.com/78699521/127746947-1885d47b-b822-4bed-9fa0-e227a0e82c11.png)







