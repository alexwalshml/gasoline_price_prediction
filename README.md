# Gasoline Price Prediction

## Problem Statement

The price of gasoline is a factor which affects millions of Americans every single day. Increases in the price can put financial stress on many people, and to make things worse its price is hard to foresee. So many factors influence the cost of gasoline, that it is nearly impossible for the average person to know what the price will be in the coming weeks, and therefore they have no way of preparing for it.

In this project, I will attempt to forecast gasoline prices using traditional techniques, such as linear projections, ARIMA, and RNNs on data such as gas and oil prices. Additionally, to try to reduce the amount of unpredictable factors that alter the cost, I will supplement my analysis with NLP techniquesn applied to news articles on the subject. These techniques combined will prove to be very effective in forecasting the price of gasoline.

## Analysis

In my analysis, I sourced data on the historical price of gasoline, three major types of oil, proved oil reserves, and inflation rates. The current gas price proved to be highly deterministic based on these factors, showing a strong linear relationship. This was a good indication that gasoline could prove to be forecastable. 

For NLP analysis, I sourced over two hundred thousand news articles from the GDELT Events database which pertained to a subject related to gas or oil. These articles were lemmatized and vectorized, then fit with random forests. Accuracy proved to be extremely low, and a cost function was implemented that heavily penalized wrong positive predictions, but barely penalized wrong neutral predictions. 

For the modeling phase, I implemented an RNN which fed into a dense network. The RNN accepted numerical data and made as good of a prediction as it could, but it alone was not especially accurate. The output of the RNN was combined with the NLP prediction, along with ARIMA and linear forescasts, and that vector was learned by the dense network. This model proved to be extremely effective, yielding a mean absolute error of $0.035 on the testing data.

## Conclusions and Recommendations

Overall, the NLP techniques I implemented were far from good enough. My crass approximations of classifying the articles based on the change in gas prices proved to be very ineffective. I still believe in the potential of NLP components in time series, but as I implemented them I think the only thing I achieved was adding a dimension of noise to my data. Going forward, the first thing I would change in this approach is to heavily search over NLP models to find one which is better than what I used. This would likely involve transfer learning with an already-advanced text classification model.

The numerical data, on the other hand, proved to be very effective with the features that I created. I would like to implement some studies to see which features where the most important, however the features engineering and dimensionality reduction I applied has been proved as a process. Going forward, I would like to implement more stochastic modeling techniques to fit into the dense network, as this would likely cover some of the weaknesses of other models.

Modeling wise, the next thing to do is to implement an autoregressive model that can forecast further into the future. A one-week forecast is far from useless, however long time spans would be interesting to see. The code as implemented can be trivially modified to do longer (one-shot) forecasts, but these would be unreliable, so I would definitely opt for autoregression going forward.

