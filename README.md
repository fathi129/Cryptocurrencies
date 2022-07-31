# Cryptocurrencies
## Overview of the Analysis
## Purpose of the Analysis
## Resources Used
## Results
### Deliverable 1: Preprocessing the Data for PCA 
Using your knowledge of Pandas, you’ll preprocess the dataset in order to perform PCA in Deliverable 2.
Follow the instructions below and use the crypto_clustering_starter_code.ipynb file to complete Deliverable 1.

Open the crypto_clustering_starter_code.ipynb file, rename it crypto_clustering.ipynb, and save it to your Cryptocurrencies GitHub folder.

Read in the crypto_data.csv to the Pandas DataFrame named crypto_df.
NOTE
The crypto_data.csv was retrieved from CryptoCompare (Links to an external site.).

Keep all the cryptocurrencies that are being traded.
Drop the IsTrading column.
Remove rows that have at least one null value.
Filter the crypto_df DataFrame so it only has rows where coins have been mined.
Create a new DataFrame that holds only the cryptocurrency names, and use the crypto_df DataFrame index as the index for this new DataFrame.
Remove the CoinName column from the crypto_df DataFrame since it's not going to be used on the clustering algorithm.
Take a moment to check that your crypto_df DataFrame looks like the image below:

Use the get_dummies() method to create variables for the two text features, Algorithm and ProofType, and store the resulting data in a new DataFrame named X.
Use the StandardScaler fit_transform() function to standardize the features from the X DataFrame.

### Deliverable 2: Reducing Data Dimensions Using PCA

Using your knowledge of how to apply the Principal Component Analysis (PCA) algorithm, you’ll reduce the dimensions of the X DataFrame to three principal components and place these dimensions in a new DataFrame.
Follow the instructions below and use the information in the crypto_clustering_starter_code.ipynb file to complete Deliverable 2.

Continue using the crypto_clustering.ipynb file from Deliverable 1 where you’ve already performed the preprocessing steps.
Using the information we’ve provided, apply PCA to reduce the dimensions to three principal components.
If you’d like a hint on how to use the PCA algorithm, that’s totally okay. If not, that’s great too. You can always revisit this later if you change your mind.
Create a new DataFrame named pcs_df that includes the following columns, PC 1, PC 2, and PC 3, and uses the index of the crypto_df DataFrame as the index.
Your DataFrame should look like the image below:



### Deliverable 3: Clustering Cryptocurrencies Using K-means

Using your knowledge of the K-means algorithm, you’ll create an elbow curve using hvPlot to find the best value for K from the pcs_df DataFrame created in Deliverable 2. Then, you’ll run the K-means algorithm to predict the K clusters for the cryptocurrencies’ data.
Follow the instructions below and use the information in the crypto_clustering_starter_code.ipynb file to complete Deliverable 3.

Continue using the crypto_clustering.ipynb file that you used in Deliverable 2 to reduce the dataset to three dimensions.
Using the pcs_df DataFrame, create an elbow curve using hvPlot to find the best value for K.
Next, use the pcs_df DataFrame to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data.
Create a new DataFrame named clustered_df by concatenating the crypto_df and pcs_df DataFrames on the same columns. The index should be the same as the crypto_df DataFrame.
Add the CoinName column that holds the names of the cryptocurrencies, which you created in Step 7 of Deliverable 1, to the clustered_df.
Add another new column to the clustered_df named Class that holds the predictions, i.e., model.labels_, from Step 3.
Your clustered_df DataFrame should look like the image below:



### Deliverable 4: Visualizing Cryptocurrencies Results

