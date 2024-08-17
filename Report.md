
**ANALYSIS REPORT** 

Purpose: The purpose of this analysis is to use past charity data in order to try and predict the success or failure of new charities. This is done by training a neural net on said past charity data. The charity data contains several variables that the neural net attempts to find patterns within. Those variables are as follows: Application type, affiliation, classification, use case, organization, status, income amount, special considerations, ask amount, and whether or not the corresponding charity was successful or not. The entire reason we want to be able to predict if a charity will be successful or not is so the entity potentially funding the charity knows how risky it would be to go through with the funding. 

Results: 

    Target -- The target for this analysis was the "is_successful" variable, as that is what we are trying to predict, whether or not a charity will be successful.

    Features -- The features for this model are all the variables that could bear some weight in the prediction. This is most of the variables, including the following: 
    
        * APPLICATION_TYPE
        * AFFILIATION
        * CLASSIFICATION
        * USE_CASE
        * ORGANIZATION
        * STATUS
        * INCOME_AMT
        * SPECIAL_CONSIDERATIONS
        * ASK_AMT   

    Removed Features: The only ones that were removed were "EIN" and "NAME" as they have no meaning when it comes to prediction. They are neither targets nor features.

    Model Architecture: Originally, the number of layers, neurons per layer, and activation functions were chosen just as standard starting points, as there was no information to go on besides the size of the dataset and the number of features. The following are the initial values: 

        Layers: 2 hidden layers + 1 output layer
        Neurons: 32, 64, and 1, respectively
        Activation functions: 'relu', 'relu', and 'sigmoid', respectively

    These settings proved to be decent, but didn't quite make it to that 75% goal.

    Performance: The initial model performed just shy of the target (75%) at a 72.83%.

    Next steps: After seeing the initial performance of the model, I tried a variety of things to make the model perform slightly better. They are as follows:

        * I changed the threshold that certain variables grouped "rare values" into one single "other" value. I did this to try to confuse the model less with rare values as it was learning the data.

        * Because there were over 30,000 rows of data, each with 9 feature variables, I tried to add more layers, as the data is complex and I thought more layers would do better at handling it. Also, after one-hot encoding, there were even more feature variables.

        * I also tried raising the number of neurons AND lowering the number of neurons. I did this because during the original model's training, the accuracy seemed to plateau after only a few epochs. As I understand it, this could be a sign of overfitting as well as underfitting, so I tried both. The .ipynb file that was submitted is the one where I increased the number of neurons, but I did try both.

        * I played around with the number of epochs and the batch size, but nothing I did, no matter how extreme, had any noticeable affect. 

        * Lastly, I also played around with different activation functions. For some of my layers, I kept 'relu', and for others, I tried another common one: 'tanh'. 

    Despite my best efforts, I couldn't get the model to increase in accuracy. In fact, I couldn't get the model to move up OR down by more than 0.5%. I would've loved to get it to work, but I'm not sure if doing so would take the model outside the scope of the assignment or not.

Summary: In summary, the model works effectively in the sense that it is better than a coin flip, but it's not high enough that I would make serious decisions based on its predictions. Even though the assignment requests a goal of 75% accuracy, if this were implemented in reality, I would probably want an accuracy closer to 85% or higher. One suggestion I have to improve on this analysis is to use a different type of model called "Random Forest." From what I've read, this type of model is better at avoiding overfitting, which I believe was a problem. This model is also good with categorical variables, which existed a lot in the charity dataset. Perhaps by tinkering with the parameters of this other model, I would be able to achieve an accuracy of over 75%, or maybe even over 85%.