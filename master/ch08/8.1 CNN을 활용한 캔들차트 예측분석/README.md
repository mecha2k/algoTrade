
## Introduction
Predict the stock market price will go up or not in the near future.

## Data Collection
- Using Yahoo! Finance for time series data source
- 50 Taiwan Companies from 0050.TW index.
- Top 10 Indonesia Stock exchange companies.

## Methodology
- Using candlestick chart for input model
- DeepCNN

### Prepare Dataset
- Convert OHLCV stock market data to Candlestickchart
```
python run_binary_preprocessing.py <ticker> <tradingdays> <windows>
```
example
```
python run_binary_preprocessing.py 2880.TW 20 50
```
- Generate dataset
```
python generatedata.py <pathdir> <origindir> <destinationdir>
```
example
```
python generatedata.py dataset 20_50/2880.TW dataset_2880TW_20_50
```
- Remove alpha channel
```
cd /dataset/dataset_2880TW_20_50
find . -name "*.png" -exec convert "{}" -alpha off "{}" \;
```

### Training
- DeepCNN
```
python myDeepCNN.py -i <datasetdir> -e <numberofepoch> -d <dimensionsize> -b <batchsize> -o <outputresultreport>
```
example
```
python myDeepCNN.py -i dataset/dataset_2880TW_20_50 -e 50 -d 50 -b 8 -o outputresult.txt
```


## Performance Evaluation
- Accuracy
- Specitivity
- Sensitivity
- MCC
- F1

## Reference
 * [Going Deeper with Convolutional Neural Network for Stock Market Prediction](https://github.com/rosdyana/Going-Deeper-with-Convolutional-Neural-Network-for-Stock-Market-Prediction)

