# Cryptocurrencies
## Overview of the Analysis
## Purpose of the Analysis

## Resources Used
*DataSources*:  [crypto_data.csv](https://github.com/fathi129/Cryptocurrencies/blob/master/Resources/crypto_data.csv)<br>
*Software used*: Jupyter Notebook <br>
*Language*: Python<br>
*Libraries*: scikit-learn,hvplot,plotly. <br>

## Results
### Deliverable 1: Preprocessing the Data for PCA 
Using the knowledge of Pandas, we will preprocess the dataset in order to perform PCA.Read in the crypto_data.csv to the Pandas DataFrame and name it as crypto_df.The crypto_data.csv was retrieved from CryptoCompare (Links to an external site.).Keep all the cryptocurrencies that are being traded.
Drop the IsTrading column.Remove rows that have at least one null value.Filter the crypto_df DataFrame so it only has rows where coins have been mined.
Create a new DataFrame that holds only the cryptocurrency names, and use the crypto_df DataFrame index as the index for this new DataFrame.
Remove the CoinName column from the crypto_df DataFrame since it's not going to be used on the clustering algorithm.
The crypto_df DataFrame looks like the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/Deliverable%201_crypto_df.png"  width = 600><br>
Using the get_dummies() method created variables for the two text features, Algorithm and ProofType, and stored the resulting data in a new DataFrame named X.Used the StandardScaler fit_transform() function to standardize the features from the X DataFrame.

### Deliverable 2: Reducing Data Dimensions Using PCA
Using the knowledge of how to apply the Principal Component Analysis (PCA) algorithm, we will reduce the dimensions of the X DataFrame to three principal components and place these dimensions in a new DataFrame.
Create a new DataFrame named pcs_df that includes the following columns, PC 1, PC 2, and PC 3, and uses the index of the crypto_df DataFrame as the index.
Your DataFrame should look like the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/Deliverable2_pcs_df.png"  width = 600><br>

### Deliverable 3: Clustering Cryptocurrencies Using K-means
Using the K-means algorithm, we will create an elbow curve using hvPlot to find the best value for K from the pcs_df DataFrame created.Then, we will run the K-means algorithm to predict the K clusters for the cryptocurrencies’ data.
Using the pcs_df DataFrame, create an elbow curve using hvPlot to find the best value for K.
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del3_Elbow_curve.png"  width = 600><br>
Next, we will use the pcs_df DataFrame to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data.
Created a new DataFrame named clustered_df by concatenating the crypto_df and pcs_df DataFrames on the same columns. The index is same as the crypto_df DataFrame.Add the CoinName column that holds the names of the cryptocurrencies, which we created already to the clustered_df.Added another new column to the clustered_df named Class that holds the predictions, i.e., model.labels_.
The clustered_df DataFrame should look like the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del3_Clustered_df.png"  width = 600><br>

### Deliverable 4: Visualizing Cryptocurrencies Results
Using the knowledge of creating scatter plots with Plotly Express and hvplot, we will visualize the distinct groups that correspond to the three principal components we created in Deliverable 2, then we will create a table with all the currently tradable cryptocurrencies using the hvplot.table() function.
Create a 3D scatter plot using the Plotly Express scatter_3d() function to plot the three clusters from the clustered_df DataFrame.
Add the CoinName and Algorithm columns to the hover_name and hover_data parameters, respectively, so each data point shows the CoinName and Algorithm on hover.<br>
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_3DScatterPlot.png"  width = 600><br>
Creatde a table with tradable cryptocurrencies using the hvplot.table() function.The table should look like the table in the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_hvplot.png"  width = 600><br>
Printed the total number of tradable cryptocurrencies in the clustered_df DataFrame.Used the MinMaxScaler().fit_transform method to scale the TotalCoinSupply and TotalCoinsMined columns between the given range of zero and one.

Created a new DataFrame using the clustered_df DataFrame index that contains the scaled data we created.Added the CoinName column from the clustered_df DataFrame to the new DataFrame.Added the Class column from the clustered_df DataFrame to the new DataFrame.YourThe new DataFrame should look similar to the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_Plot_df.png"  width = 600><br>
Created an hvplot scatter plot with x="TotalCoinsMined", y="TotalCoinSupply", and by="Class", and it shows the CoinName when we hover over the the data point.The scatter plot should look similar to the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_scatterplot.png"  width = 600><br>

