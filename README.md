# Recommendations with IBM
We use the IBM Watson Studio Platform user and articles information to explore various methods for recommending an article to a particular user. Different approaches are needed if the user already has a interaction history on a platform or if the user is a first time user. We will go through them in the notebook

## Files
```
root
|
|-- Recommendations_with_IBM.ipynb  # main project notebook
|-- project_tests.py                # Make sure the results are correct
|-- top_5.p                         # data used by the test
|-- top_10.p                        # data used by the test
|-- top_20.p                        # data used by the test
|-- user_item_matrix.p              # copy of user-item matrix
|
+-- data
    |-- articles_community.csv      # info for the articles on the platform
    |-- user-item-interactions.csv  # info for the user articles interactions
|-- README.md
```

## Processes
We implement the following two recommendation techniques

### Rank based recommendations.
In a rank based recommendation, the system ranks the "items" (movies/books/products) according to the ratings they have recieved from the users. Since the articles on the platform did not have ratings from the users we rank them according to the number of times they have been interacted with and recommend the top articles for a user.

### User-User Based Collaborative Filtering.
For a collaborative filtering approach for recommendation we match the users past interactions with the articles and compare it with other users interactiions. The other users are then ranked based on similar interactions histories. We then get the list of articles the user has not visited and recommend them. 

### Matrix Factorization
We create the "user-item matrix" and perform Singular Value Decomposition by providing a number of latent features we want to extract from the matrix. The optimum number of latent features is found out by carrying out SVD for different number of latent features and finding out the accuracy at each step. The number of latent features with the lowest accuracy is chosen.

### Content Based Filtering (Not explored here)
The items can be filtered based on their content. The items with the most similar content to the item the users has already interacted with can be ranked. Then the articles which the users has not interacted with can be recommended.

## How useful were the recommendations
To find out if the recommendations were useful, A/B testing has to be performed on the platform for a specific number of days and see how the users respond to the recommendation coming from the system.
