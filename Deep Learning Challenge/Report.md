# Neural Network Model

## Model Architecture
Non-profit Alphabet Soup Foundation would like a tool which classifies funding applicants to identify those who if granted funding by the foundation would have highest likelihood of success in their ventures.

Alphabet Soup has provided a CSV containing the data of more than 34,000 organisations that have received funding in the past from Alphabet Soup in the past. Within this dataset are a number of columns that capture metadata metrics about each organisation, such as:

EIN, NAME, APPLICATION_TYPE, AFFILIATION (Industry), CLASSIFICATION (Government organisation classification), USE_CASE (Use case for funding), ORGANIZATION (Organisation type), STATUS (Active status), INCOME_AMT (Income classification), SPECIAL_CONSIDERATIONS (Special considerations for application), ASK_AMT (Funding amount requested) & IS_SUCCESSFUL (Was the funding venture successful).

## Data Preprocessing
The dataset was preprocessed by:
- Dropping out the EIN and NAME. Removing these detail alllows us to deidentify the data and remove noise from the model.
- Binning the of the APPLICATION_TYPE allows for lower frequency funding requests to be grouped in "Other" as  category, to ensure outliers do not skew the model.
- Binning the CLASSIFICATION likewise will allow for classification outliers to be grouped in "Other" as a category.
- Encoding the categorical variables using get.dummies() function, will creates numerical binary variables for each category, which can be used, understood more easily by the model.
- Scaling the numerical variables using StandardScaler() function, ensure that the numerical variables are on the same scale and amplitude, to avoid more weight being disproportionately skewed towards certain features.

## Compiling, Training, and Evaluating the Model
The model was compiled using the following parameters:
- Preprocessed data was divided into training and testing datasets using sklearn.model_selection.train_test_split() function. The training dataset was used to train the model, and the testing dataset was used to evaluate the model.
- The model was compiled using the Sequential() function, with performance  adjustments made to the following parameters:
    - Split and Train sample size (0.1 - 0.3 trialed)
    - Number of input features (2 - 56 were trialed)
    - Scaler (Removal of Scaler was trialed)
    - Number of hidden layers (1- 5 layers were trialed)
    - Number of Neurons (6 - 800 were tested)
    - Activation function of hidden layers (sigmoid, tanh, relu were trialed)
    - Activation function of output layer (sigmoid, tanh, relu were trialed)
    - Number of epochs (30 - 900 were trialed)


    * The loss function was fixed as a binary_crossentropy, optimized with adam.
    * The model was then evaluated using the loss and accuracy metrics.

    ## Summary
    * The model hovered around 72%-73% accuracy, with a loss of 0.56-0.55.
    * Removal of the Scaler did not improve the model performance, dropping accuracy to 53% and loss to 0.69.
    * Increasing the number of hidden layers to 5, and the number of neurons to 800, improved the model performance to 73% accuracy and 0.55 loss.
    * Adjustment of metrics within the model had very little impact on the model performance.
    * The model was unable to achieve the target performance of 75% accuracy, and 0.45 loss.

    ## Recommendation
    * A better understanding of the raw data would be required to gain a better understand in developement and selection of an appropriate model to achieve the targeted  performance metrics.
    * Given the large number of model options available, I question ifthis data (once a greater understanding has been gained), may fair better with one of the other models structures.