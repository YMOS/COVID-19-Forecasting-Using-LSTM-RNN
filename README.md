# COVID-19-Forecasting-Using-LSTM-RNN
Repository for forecasting of COVID-19 spread using LSTM RNN

# Objective
Researchers, doctors and epidemiologist around the world have joined hands to accelerate the process of finding an effective vaccine to fight the ongoing global pandemic of nCOV-19 virus ("Novel Coronavirus (2019-nCoV) situation reports", 2020). However, it is estimated that the process of coming up with a medically approved vaccine will take around 6 months after undergoing all the required trials. With a vaccine to fight the global pandemic of nCOV-19 still in the development pipeline, this creates an interesting use-case of determining the further spread of the virus.

# NOTE
It is extremely important to note that the analysis cannot be considered as a baseline for any medical diagnosis or study

# Data Source
The data for the analysis is sourced from data repository for 2019 Novel Coronavirus Dashboard operated and maintained by John Hopkins University Center for Systems Science and Engineering (JHU CCE) (“CSSEGISandData”,2020). The dataset consists of 3 sub-datasets of confirmed corona cases, death cases and recovered cases on each day basis. The data for all the 3 sub-datasets consisted of data from 22nd January 2020 to 13th March 2020. There is a total of 56 data points in the dataset where each data point corresponds to the count of confirmed cases, death cases and recovered cases at the end of each day.

# LSTM Model Used
The specification of configuration for the LSTM model are as follows:

+ Stateful = true: Since the sequence of observation in time-series is important, a stateful LSTM model will use the output from the previous sample as the initial state for the next sample.

+ Input format (samples, timesteps, features): 3D array with the sample as the number of observations in each batch, timesteps is the lookback value and features are 1 for univariate time-series. For training, the input format was (34,3,1) i.e. 34 entries with 3
days of lookback and 1 feature.

+ Loss: The loss function used for each pass is mean square error 

+ Optimizer: Adaptive Monument Estimation (ADAM) optimizing algorithm used to minimize the loss in each pass.

+ Metrics: Accuracy is used as the metric to assess the model performance.

+ Epochs: The number of forward or backward passes or iteration. For the analysis, it was set to 100. Increase in epoch value increases the model performance but require more processing power.

# Results

The LSTM model trained on 34 observation showed an excellent performance in forecasting the nCOV-19 spread for test data without any overfitting. The performance of the LSTM model for China using the Root Means Squared Error (RMSE) evaluation metric on test data was 0.029

# References
CSSEGISandData. (2020, April 9). CSSEGISandData/COVID-19. Retrieved from https://github.com/CSSEGISandData/
