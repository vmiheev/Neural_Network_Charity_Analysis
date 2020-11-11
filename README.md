# Neural_Network_Charity_Analysis

## Overview

Utilizing a deep learning model to predict the success of investments into charities. This information is used to pinpoint the foundations to provide money to. The target model performance is 75%.

## Results

### Data Preprocessing

* The IS_SUCCESSFUL variable is considered the target of the model.
* The APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, and ASK_AMT variables are considered the features of the model.
* The EIN and NAME variables have been removed from the data as they are neither target or features.

### Compiling, Training, and Evaluating the Model

* There are 4 layers in the deep learning model: the input layer, two hidden layers, and an output layer.
* The input layer has 43 input features to match the number of OneHotEncoded features.
* The first hidden layer has 80 neurons and uses the ReLU activation function - this is approximately double the input features and eliminates negative results from the function.
* The second hidden layer has 30 neurons and uses the ReLU activation function - this is approximately half of the features being passed into the layer and uses a second ReLU function to search for links between the two layers.
* None of the models were able to achieve the target model performance of 75%.
* The initial model had the greatest merit of predicting charity investment success at 73.15%:

![1](/Results/model1.png)

* The first attempt to optimize the model increased the number of neurons in the first hidden layer to exactly double the input features, and the neurons in the second hidden layer to exactly half of those. The first hidden layer activation function was changed to a linear function to allow for a greater range of outputs and see if it would effect the results.
* The first optimization attempt performed slightly worse with a success rate of 73.04%:

![2](/Results/model2.png)

* Additionally, a random forest model was used to rank feature importances in order to make the decision on which features to remove from the model:

![importances](/Results/importances.png)

* The second attempt to optimize the model bucketed the data with frequencies under 100 in the AFFILIATION feature into the "Other" category, as well as dropping the INCOME_AMT, SPECIAL_CONSIDERATIONS and STATUS features as they were deemed to have a low impact on the model. The neurons in the hidden layers were dropped to 60 and 30 respectively to be roughly double the input features.
* The second optimization attempt performed slightly worse with a success rate of 72.98%:

![3](/Results/model3.png)

* The third attempt to optimize the model dropped the USE_CASE feature in addition to the previous drops. An additional hidden layer was added using the ReLU activation function. Neurons were increased to three times the input features in the first hidden layer at 72, with neurons being halfed in each subsequent layer.
* The third optimization attempt performed slightly worse with a success rate of 72.90%:

![4](/Results/model4.png)

## Summary

* Overall, the first model provided the best results, with subsequent models providing slightly worse results. However, the results were not greatly varied, with the difference in success between the best and worst model being 0.25%.
* A Random Forest Classifier is another model option for this classification problem. This is because the structure of this model is similar to that of neural networks. An attempt was made to implement it but this did not result in an improvement.
* An additional approach to this problem could convert the INCOME_AMT feature to a numerical field and create a new feature that would show the ASK_AMT as a percentage of the INCOME_AMT.
