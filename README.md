# Cryptocurrencies
Discover the trends of Cryptocurrency and convince the firm to invest on the new currencies.

## Overview of the Analysis
The Analysis uses unsupervised learning algorithm In supervised learning, the input data already has a paired outcome, which is plugged in to train the model to predict outcomes in new datasets. For example, we want to build a model that, when given unfamiliar data, can accurately predict the outcomes.
In unsupervised learning, there are two key differences from the above approach they are there are no paired inputs and outcomes,The model uses a whole dataset as input.Unsupervised learning is used in one of the following two ways Transform the data to create an intuitive representation for analysis or to use in another machine learning model; or Cluster or determine patterns in a grouping of data, rather than to predict a classification.
Before moving data to the unsupervised algorithms, we need to prepare the data by doing the following steps Data selection,Data processing and Data transformation.Then we will use the algorithms.Clustering is a type of unsupervised learning that groups data points together. This group of data points is called a cluster.One of the most popular ways to cluster is by using the K-means algorithm.K-means is an unsupervised learning algorithm used to identify and solve clustering issues.K represents how many clusters there will be. These clusters are then determined by the means of all the points that will belong to the cluster.An easy method for determining the best number for K is the elbow curve. Elbow curves get their names from their shape: they turn on a specific value, which looks a bit like an elbow.PCA is a statistical technique to speed up machine learning algorithms when the number of input features (or dimensions) is too high. PCA reduces the number of dimensions by transforming a large set of variables into a smaller one that contains most of the information in the original large set.

## Purpose of the Analysis
The popularity of Bitcoin caused a price jump that makes it unaffordable for many new investors.However there are many cryptocurrencies available at affordable prices.We will analyze the trends of Cryptocurrency using unsupervised machine learning algorithms.Unsupervised machine learning is used when there is known output.It is used to discover the patterns or groups in data.It uses only input data.

## Resources Used
*DataSources*:  [crypto_data.csv](https://github.com/fathi129/Cryptocurrencies/blob/master/Resources/crypto_data.csv)<br>
*Software used*: Jupyter Notebook <br>
*Language*: Python<br>
*Libraries*: scikit-learn,hvplot,plotly. <br>

## Results
### Deliverable 1: Preprocessing the Data for PCA 
Using the knowledge of Pandas, we will preprocess the dataset in order to perform PCA.Reading in the crypto_data.csv to the Pandas DataFrame and named it as crypto_df.The crypto_data.csv was retrieved from CryptoCompare (Links to an external site).By keeping all the cryptocurrencies that are being traded,
Droping the IsTrading column,Removing rows that have at least one null value,Filtering the crypto_df DataFrame so it only has rows where coins have been mined,a new DataFrame was created that holds only the cryptocurrency names, and use the crypto_df DataFrame index as the index for this new DataFrame.
By removing the CoinName column from the crypto_df DataFrame since it's not going to be used on the clustering algorithm.
The crypto_df DataFrame looks like the image below:<br>
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/Deliverable%201_crypto_df.png"  width = 600><br>
Using the get_dummies() method created variables for the two text features, Algorithm and ProofType, and stored the resulting data in a new DataFrame named X.Used the StandardScaler fit_transform() function to standardize the features from the X DataFrame.

### Deliverable 2: Reducing Data Dimensions Using PCA
Using the knowledge of how to apply the Principal Component Analysis (PCA) algorithm, we will reduce the dimensions of the X DataFrame to three principal components and place these dimensions in a new DataFrame.Created a new DataFrame named pcs_df that includes the following columns, PC 1, PC 2, and PC 3, and used the index of the crypto_df DataFrame as the index.
The pcs_df DataFrame should look like the image below:<br>
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/Deliverable2_pcs_df.png"  width = 400><br>

### Deliverable 3: Clustering Cryptocurrencies Using K-means
Using the K-means algorithm, we will create an elbow curve using hvPlot to find the best value for K from the pcs_df DataFrame created.Then, we will run the K-means algorithm to predict the K clusters for the cryptocurrencies data.Using the pcs_df DataFrame, created an elbow curve using hvPlot to find the best value for K.<br>
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del3_Elbow_curve.png"  width = 800><br>
Next, we will use the pcs_df DataFrame to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data.
Created a new DataFrame named clustered_df by concatenating the crypto_df and pcs_df DataFrames on the same columns. The index is same as the crypto_df DataFrame.Added the CoinName column that holds the names of the cryptocurrencies, which we created already to the clustered_df.Added another new column to the clustered_df named Class that holds the predictions, i.e.,model.labels_.
The clustered_df DataFrame should look like the image below:<br>
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del3_Clustered_df.png"  width = 700><br>

### Deliverable 4: Visualizing Cryptocurrencies Results
The scatter plots has been created using with Plotly Express and hvplot, we will visualize the distinct groups that correspond to the three principal components we created in Deliverable 2, then we will create a table with all the currently tradable cryptocurrencies using the hvplot.table8) function.
Created a 3D scatter plot using the Plotly Express scatter_3d() function to plot the three clusters from the clustered_df DataFrame.
Added the CoinName and Algorithm columns to the hover_name and hover_data parameters, respectively, so each data point shows the CoinName and Algorithm on hover.<br>
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_3DScatterPlot.png"  width = 800><br>
Created a table with tradable cryptocurrencies using the hvplot.table() function.The table looks like the table in the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_hvplot.png"  width = 800><br>
Printed the total number of tradable cryptocurrencies in the clustered_df DataFrame.<br>
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_printcount.png"  width = 800><br>
Used the MinMaxScaler().fit_transform method to scale the TotalCoinSupply and TotalCoinsMined columns between the given range of zero and one.
Created a new DataFrame using the clustered_df DataFrame index that contains the scaled data we created.Added the CoinName column from the clustered_df DataFrame to the new DataFrame.Added the Class column from the clustered_df DataFrame to the new DataFrame.The new DataFrame looks similar to the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_Plot_df.png"  width = 600><br>
Created an hvplot scatter plot with x="TotalCoinsMined", y="TotalCoinSupply", and by="Class", and it shows the CoinName when we hover over the the data point.The scatter plot should look similar to the image below:
<img src = "https://github.com/fathi129/Cryptocurrencies/blob/master/Screenshots%20of%20Cryptocurrency/del4_scatterplot.png"  width = 700><br>

