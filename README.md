# Social-demographic data analisys

The aim of the project is to fill missing user data.


## Exploration

The first step was to visualize the distribution of the user fields. This first step allowed to detect there were almost 1% of missing values for the zipcode field. The missing zipcode could be represented as a NaN or with zero value. Also it appears that year of birth and gender missing values where not synchronized meaning there could be a gender value but a missing year of birth and vice-versa. This implies the need to produce two distinct models to predict year of birth and gender. From the gender distribution, we can see that there are more man than women in the dataset.

At the end of this stage, I thought it would be better to predict first the gender missing values and then used those predicted missign values to predict the year of birth. Indeed, I thought the gender could influence the year of birth target variable.

## Gender modelisation

The features used for this model are the zipcode, the firstname and the domain. The zipcode will be introduced in the model as a numerical features. The missing zipcode values are replaced by the mean observed in the dataset. The firstname and the domain having a high cardinality, I chose to encode them using gray encoding (similar to binary encoding). 

For the model, I chose to use a shallow neural network with 2 hidden layers. The Adam optimizer is used and the CyclicLR implementation is used to improve convergence. To avoid overfitting, early stopping callback is used.

I achieved a 93% accuracy on the validation set.

## Year of birth modelisation

The features used for this model are the zipcode, the firstname, the domain and the predicted gender. The zipcode will be introduced in the model as a numerical features. The missing zipcode values are replaced by the mean observed in the dataset. The firstname and the domain having a high cardinality, I chose to encode them using gray encoding (similar to binary encoding). 

For the model, I chose to use a shallow neural network with 2 hidden layers. The Adam optimizer is used and the CyclicLR implementation is used to improve convergence. To avoid overfitting, early stopping callback is used.

I achieved a mean absolute error of 8 years on the validation set.



