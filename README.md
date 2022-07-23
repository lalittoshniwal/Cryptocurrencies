# Cryptocurrencies

## Purpose
The purpose of this exercise was to prepare an analysis for an investment bank who is preparing to get into the cryptocurrency market. The bank is interested in offering a new cryptocurrency investment portfolio for its customers. However, the company is lost in the vast universe of cryptocurrencies. I was tasked to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

The data I provided was not ideal, so it needed to be processed to fit the machine learning models. Since there is no known output I decided to use unsupervised learning. To group the cryptocurrencies, I decided on a clustering algorithm. I then used data visualizations to share my findings with the board.

## Analysis
1. I first preprocessed the data for for Principal Component Analysis (PCA). The following five preprocessing steps were performed on the DataFrame that was created by reading in provided CSV:
    - All cryptocurrencies that are not being traded were removed
    - The IsTrading column was dropped
    - All the rows that have at least one null value were removed
    - All the rows that do not have coins being mined were removed
    - The CoinName column was dropped

<img src="/Resources/crypto_df.png" >

    In addition following steps were performed to prep the data:
    - A new DataFrame was created that stores all cryptocurrency names from the CoinName column and retains the index from the crypto_df DataFrame
    - The get_dummies() method was used to create variables for the text features, which were then stored in a new DataFrame, Features
    - The features from the Features DataFrame were standardized using the StandardScaler fit_transform() function

2. Next, I reduced data dimensions using PCA. I reduced the dimensions of the Features DataFrame down to three principal components.

<img src="/Resources/pcs_df.png" >

3. I then used the K-means algorithm to create an elbow curve using hvPlot to find the best value for K from the new_pcs_df DataFrame I created above. Then, I ran the K-means algorithm to predict the K clusters for the cryptocurrencies’ data. I also created a new DataFrame named clustered_df by concatenating the crypto_df and new_pcs_df DataFrames on the same columns.

<img src="/Resources/elbow_cruve.png" >

<img src="/Resources/clustered_df.png" >

4. I then visualized the results as follows:
    - The clusters was plotted using a 3D scatter plot, and each data point shows the CoinName and Algorithm on hover

<img src="/Resources/cluster_plot.png" >

    - A table with tradable cryptocurrencies was created using the hvplot.table() function

<img src="/Resources/hvplot_table.png" >

    - A DataFrame was created that contains the clustered_df DataFrame index, the scaled data, and the CoinName and Class columns

<img src="/Resources/final_df.png" >

    - A hvplot scatter plot was created where the X-axis was "TotalCoinsMined", the Y-axis was "TotalCoinSupply", the data was ordered by "Class", and it showed the    CoinName when hover over the data point

<img src="/Resources/hvplot_scatter.png" >

## Conclusion

