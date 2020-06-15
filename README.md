# Kaggle-Walmart-Sales-Forecasting-Model
Jupyter Notebook for Walmart Kaggle Challenge

Trained a supervised ML algorithim to forecast store sales of Walmart.
The kaggle Challenge https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting

As I am sure you have been told before Kaggle is huge Machine Learning knowledge pool and hugely beneficial both to people dipping their toes in this vast ocean and experienced campaigners alive. Boosted by huge community that always takes time to help others, frankly the resources are endless for competitions, datasets, public kernels you name it.
This particular blog covers my experience with doing Sales Forecasting for a Kaggle Challenge sponsored by Walmart to seek prospective ML engineers.
https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting
”Historical sales data for 45 Walmart stores located in different regions. Each store contains many departments, and participants must project the sales for each department in each store. To add to the challenge, selected holiday markdown events are included in the dataset. These markdowns are known to affect sales, but it is challenging to predict which departments are affected and the extent of the impact.”

- Loading the Data
Data is contained in zip files so you need to extract them before using loading them into dataframes using pandas and yes remember to decode using the correct format or you will end up with a pile of gibberish. You can now take a peep into your dataframes to get an idea of what you are dealing with and getting an idea of about their shape is also an good idea. So while performing feature engineering you have a fair idea about the number of edit operations you will be performing.

- Merging the DataFrames
Here I have merged the dataframes on Store and Date columns and have converted the Data column into a pandas datatime format and the reason for it will become more clear as we move ahead in the process.

- Visualizations and EDA
Create some basic scatter plots using matplotlib so we can better understand the relationships of the variables with our Target variable.

- One Hot Encoding
Here after one hot encoding the appropriate variables I have removed Columns missing from the test data, repeated modelling with various combinations also showed Markdown3 adds very little variance to our data hence removing it.

- Train and Validation split
Creating a 80–20 split between training and validation dataset and assigning extra weights to data samples falling to holiday dates.

- Train XGBoost
Initialize D matrices required for XGBoost and define a dictionary for the various hyper parameters and make the model stop after 20 iterations of seeing no improvement in the mean absolute error. You can follow that and get an R2 score on evaluation dataset and see how much variance is explained by your data and current features. I got an score of 0.92 which is quite good so I proceeded to to prepare my model for prediction on test dataset.

- Submission and Public Score
You can submit the solution dataframe to Kaggle Challenge link to get your public score. I got a WMAE of around 3K which places me in favorable position compared to top position(2.1K) more so when you consider he made around 250 submissions for this and I made just 41.
I will be posting the link to my GitHub repo below with the entire code and where I trained additional GBM like CatBoost, Light GBM , Random Forrest. I didn't include them here for the sake of brevity of this post. You can improve on this by performing hyper parameter optimization using libraries like HyperOPT or perform better feature engineering.
