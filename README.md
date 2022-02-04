# Neural Network Charity Analysis

## Overview of the Neural Network Charity Analysis

Beks is a data scientist and programming for the non-profit foundation AlphabetSoup. Beks has requested my help analyze the impact of AlphabetSoup’s donations, to ensure the foundations money is being used effectively. I will assist Beks in creating a deep learning Neural Network model, and we will be able to use a mathematical data driven solution to accurately determine which organizations are worth donating to and which are too high risk.

## Resources
- Data Source: charity_data.csv
- Software: Python 3.9.6, Conda 4.10.3, Scikit-learn 1.0.1, Tensorflow 2.9.0, Keras-tuner 1.1.0

## Results:

After we analyze the data and finish building, compiling, and testing our neural network model we are able to answer the following questions based on the results.

### Data Preprocessing
- What variable(s) are considered the target(s) for your model?

The “IS_SUCCESSFUL” column is considered the target for the model, and the data is already displayed numerically as 1 or 0, for successful or unsuccessful donations.

- What variable(s) are considered to be the features for your model?

The “APPLICATION_TYPE“, “AFFILIATION“, “CLASSIFICATION“, “USE_CASE“, “ORGANIZATION“, “STATUS“, “INCOME_AMT“, “SPECIAL_CONSIDERATIONS“, and “ASK_AMT“ columns are considered the features for the model. Containing both numerical, and categorical data which we transformed into numerical data using OneHotEncoder.

- What variable(s) are neither targets nor features, and should be removed from the input data?

The “EIN” and “NAME” columns are neither targets nor features for the model, as they are only identification information, and they were removed accordingly from the data before executing the model.

### Compiling, Training, and Evaluating the Model

- How many neurons, layers, and activation functions did you select for your neural network model, and why?

The initial neural network model that was selected was made of two hidden layers, of 80 and 30 neurons respectively, which used the “relu” activation function, and an output layer with 1 neuron which used the “sigmoid” activation function. I wanted to start off with a deeper than one hidden layer neural network, as we have a complex data set, but also remain conscious of computation time. The number of neurons were chosen as 80 for the first layer, which is just under double the number of features being passed as inputs (43), and 30 for the second layer as the subsequent layers can typically have fewer neurons for shorter computation time without sacrificing accuracy. The “relu” activation function was chosen as it is simple, inexpensive training with generally good performance.

- Were you able to achieve the target model performance?

The model was evaluated with an accuracy of approximately 72.6%. As we were aiming for a model accuracy of 75% or higher, we can say that this model did not meet the target performance.

- What steps did you take to try and increase model performance?

In an attempt to improve the model’s performance, I rebuilt the model using the keras_tuner library to test for the highest accuracy. I ran a simulation, testing for the best accuracy, of models with 1-7 hidden layers using 50-200 neurons for the first layer and 5-100 neurons any subsequent layers and cycling through the ”relu”, “sigmoid”, and “tanh” activation functions. The keras_tuner produced a model with hyper parameters which would improve the model’s accuracy. This new model contained 4 hidden layers of 150, 85, 25, and 100 neurons respectively and used the “relu” activation function. After testing the new model was evaluated with an accuracy of 73.0%. I then attempted to make some changes to the data, in order to remove some of the clutter and increase the model’s accuracy. I altered the number of features by removing some potentially redundant columns, as well as attempting to restructure the binning of the columns with a high number of unique categorical data, but all of these attempts proved moot as I was unable to increase the model’s accuracy any further.

## Summary: 

I created a deep neural network classification model that predicts loan applicant success given the charity_data.csv dataset with 73% accuracy. This did not meet the target of 75% accuracy, and the optimization methods were unable to show any significant improvements. I would recommend attempting a different supervised machine learning model to try and reach our target accuracy level. Since we are looking for a model with binary classification, I would suggest starting with the Random Forest Classifier model and evaluate it’s performance against the deep learning model.
