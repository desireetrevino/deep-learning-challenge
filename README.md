# deep-learning-challenge
Machine Learning and Neural Networks: Binary classifier to predict success if funding is received.

# Report

## Overview of the Analysis

The purpose of this analysis was to create a binary classifier to select the applicants for funding with the best chance of success in their ventures for the nonprofit foundation Alphabet Shoup

The information included in our dataset, with more than 34,000 organizations was:
* EIN and NAME — Identification columns
* APPLICATION_TYPE — Alphabet Soup application type
* AFFILIATION — Affiliated sector of industry
* CLASSIFICATION — Government organization classification
* USE_CASE — Use case for funding
* ORGANIZATION — Organization type
* STATUS — Active status
* INCOME_AMT — Income classification
* SPECIAL_CONSIDERATIONS — Special considerations for application
* ASK_AMT — Funding amount requested
* IS_SUCCESSFUL — Was the money used effectively


A Sequential Keras Model was used, with the following optimization techniques applied to improve the model:

  * Two types of binning were tested, first try grouped onto Other the APPLICATION_TYPE with less than 1,100 organizations and the CLASSIFICATION with less than 1,000. This was adjusted to group those with less than 100 organizations onto the category "Other" during the optimization.

  * A method with hyper-parameter options to choose the activation function, number of neurons in first layer and number of hidden layers and neurons in them was created to optimize the model.

  * Kerastuner library was used to find the best model

  * Number of epochs was adjusted from 10 to 20 


## Results

**First model:**
 * 10 epochs and 3 layers with the following characteristics:
	> layer1: relu activation, 8 nodes
	> layer2: relu activation, 5 nodes
	> layer3: sigmoid activation, 1 node
	

Achieved results:
Loss: 0.5628802180290222, Accuracy: 0.7239649891853333


**Final optimized model:**

 * Did 60 trials and used the following parameters in the best model found:

>'activation': 'tanh',
> 'first_units': 3,
> 'num_layers': 2,
> 'units_0': 3,
> 'units_1': 1,
> 'units_2': 1,
> 'units_3': 7,
> 'units_4': 5,
> 'tuner/epochs': 20,
> 'tuner/initial_epoch': 7,
> 'tuner/bracket': 2,
> 'tuner/round': 2,
> 'tuner/trial_id': '0015'

Achieved results: 
* Loss: 0.5592498779296875 
* Accuracy: 0.7281632423400879

## Summary

Even after applying several optimization techniques to the model, there is little difference between our first model and the final, optimized, one. Next steps could be to explore different models, like functional API that is stronger than Sequential and creates more flexible models, or other ML API like Amazon or Google's.


