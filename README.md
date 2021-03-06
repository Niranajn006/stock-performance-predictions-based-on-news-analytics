# Stock Performance Predictions based on News Analytics
Project ID: 201812-23  
Member: Fan Gao (fg2432), Connor Gatlin (ceg2195), Ruisi Wang (rw2720)

## Summary
Historically, news and stock performance are highly correlated. In this analysis, we worked with a large uncensored dataset in an attempt to uncover the predictive power of market and news analytics. One challenge is that we had to plow through the data carefully, weed out data errors and impute missing values. Another challenge is the computational burden as the calculation wouldn't easily fit into the memory of a VM with 32GBs of memory. We had to carefully slice the data, recycle variables and collect unused space to avoid memory errors. For a memory hungry model like LSTM, both training and inference had to be done in batches. 

The results are encouraging as they show great improvements over the benchmark. Features from market data such as previous returns and prices have more significance in the models, contributing almost two thirds of the predictive power of the model. Features from news data further enhance the performance by about 35\%. As for model selections, gradient boosted trees show better performance than neural network. This could be due to overfitting or suboptimal look back window in the LSTM model. Tuning the LSTM model is beyond the scope of this project. Rather than picking the best model, we think data preprocessing and feature engineering play a bigger role in determining the final performance. Some extreme outliers could have compromised the out-of-sample performance of the models if they hadn't been treated with caution. We conclude that news data indeed add value to stock performance predictions and in conjunction with market data, it shows great improvement over the benchmark.

## Data
The data includes a subset of US-listed instruments. The set of included instruments changes daily and is determined based on the amount traded and the availability of information. This means that there may be instruments that enter and leave this subset of data. There may therefore be gaps in the data provided, and this does not necessarily imply that that data does not exist (those rows are likely not included due to the selection criteria). The market data contains a variety of returns calculated over different timespans. All of the fields in Market Data are shown in the report. The data covers period between 2007 to 2018. In total, there are 4,072,956 samples in the training data.

The news data contains information at both the news article level and asset level (in other words, the table is intentionally not normalized). All of the fields in News Data are shown in the report. The data covers period between 2007 and 2018. In total, there are 9,328,750 samples in the training data. 

Data is not uploaded to github due to copyright. You can find the dataset in [Kaggle's Two Sigma competition](https://www.kaggle.com/c/two-sigma-financial-news).

## Visualization
The web visualization code is under ./web. For selected company, we show stock prices and technical indicators on the left panel and news headlines and sentiments associated with the company on the right panel.

Example: Apple's stock prices and news analytics:
![Example: Apple's stock prices and news analytics](https://github.com/Sapphirine/stock-performance-predictions-based-on-news-analytics/blob/master/web/Website.png)

## Modeling
The modeling code is under ./src. Since LSTM has different data preprecessing requirements than gradient boosted trees, we have two separate codebases. You can find CatBoost Classifier and LightGBM in [project.ipynb](https://github.com/Sapphirine/stock-performance-predictions-based-on-news-analytics/blob/master/src/project.ipynb) and LSTM in [LSTM_final.ipynb](https://github.com/Sapphirine/stock-performance-predictions-based-on-news-analytics/blob/master/src/LSTM_final.ipynb).

## Report
The [report](https://github.com/Sapphirine/stock-performance-predictions-based-on-news-analytics/blob/master/Report.pdf) documents all the details of our analysis.

## Presentation Slides
Slides used in the presentation can be found [here](https://github.com/Sapphirine/stock-performance-predictions-based-on-news-analytics/blob/master/Presentation.pdf).

## Youtube Video
[Proposal](https://www.youtube.com/watch?v=sY_Bxfj1V-Y&t=10s)

[Demo](https://youtu.be/8oagRyBbris)
