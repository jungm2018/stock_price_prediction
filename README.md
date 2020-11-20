# stock_price_prediction
Stock price movement direction predictor (Summer Toy Project)

This was a summer toy project for analyzing stock price action/movement in the Korean Stock Exchange (KOSPI and KOSDAQ). Much like the rest of the world, there was a great bullish run after 2020 COVID-19 Market Crash, which first motivated me into researching if there were patterns in stock prices. Results were inconclusive at best (and if it were, it I would've become a millionaire)

# K-means + Support Vector Machines Approach:

Attempts to see if particular clutsering of price action results in a bias towards a particular 
price action. For example, certain candle formations are said to be associated with certain price 
action. eg. 'Descending/Ascending Triangle', 'wedge', trending up, trending down. etc. Note only price was used (no volume, technical indicators, etc)

30 days of price data was used for each training/testing case.

K-means clustering couldn't find significant bullish patterns, but Cluster 4 (downward trending)
has an average growth rate of -1.9%

Then, we use Support Vector Machine (SVM) to prediction price action movement. Best performance was 
Clutser 2 and 4, which had the following:

Cluster Number: 2 Cluster Size: 674
              precision    recall  f1-score   support

         0.0       0.70      0.79      0.74       400
         1.0       0.62      0.51      0.56       274

    accuracy                           0.67       674
   macro avg       0.66      0.65      0.65       674
weighted avg       0.67      0.67      0.67       674

Cluster Number: 4 Cluster Size: 809
              precision    recall  f1-score   support

         0.0       0.57      0.83      0.68       451
         1.0       0.51      0.22      0.31       358

    accuracy                           0.56       809
   macro avg       0.54      0.53      0.49       809
weighted avg       0.55      0.56      0.51       809

# Support Vector Machines Approach:

Similar to the K-means approach, but with multiple technical indicators as features.
This time tested with several large-cap stocks in KOSPI, with the best being KG, which had the following characteristics:

Testing on: ./KG_DATA.csv
Test size: 0.200000
Number of days predicted: 4
Window size: 30
Trained on Samples 434
Testing Result:
              precision    recall  f1-score   support

         0.0       0.53      0.66      0.59        53
         1.0       0.58      0.45      0.51        56

    accuracy                           0.55       109
   macro avg       0.56      0.55      0.55       109
weighted avg       0.56      0.55      0.55       109


# Sliding Window Approach:

Sliding window approach was unsuccessful. The idea was to find new SVM parameters for a specific time frame, to capture short term trends. Was too computationally expensive, and I couldn't implement properly.

# CNN + Grammian Angular Difference Field

Tried to use image recognition methods to predict stock prices. Converted time series images to Grammian Angular Difference and Summation Fields (to make into 2D images). This was a naive Approach to this paper: 
http://www.ieee-jas.org/fileZDHXBEN/journal/article/zdhxbywb/2020/3/PDF/JAS-2019-0392.pdf

I was able to make the GADF, GASF images but the CNN was unsuccessful.
Grammian Make generates the images, and CNN used to predict price action.