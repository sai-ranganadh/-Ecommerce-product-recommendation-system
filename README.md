# Ecommerce-product-recommendation-system

Product Recommendation System is a machine learning-based project that provides personalized product recommendations to users based on their browsing and purchase history. The system utilizes collaborative filtering and content-based filtering algorithms to analyze user behavior and generate relevant recommendations. This project aims to improve the overall shopping experience for users, increase sales for e-commerce businesses

## Dataset

Used an amazon dataset on user ratings for electronic products, this dataset doesn't have any headers. To avoid biases, each product and user is assigned a unique identifier instead of using their name or any other potentially biased information.
You can find the [dataset](https://www.kaggle.com/datasets/vibivij/amazon-electronics-rating-datasetrecommendation/) here - <https://www.kaggle.com/datasets/vibivij/amazon-electronics-rating-datasetrecommendation/download?datasetVersionNumber=1>

## Approach

- Rank Based Product Recommendation
  
  -  Objective -
      -  Recommend products with highest number of ratings.
      -  Target new customers with most popular products.
      -  Solve the Cold Start Problem
         ## Cold Start Problem:
            -  The cold start problem is a challenge faced by recommender systems. It occurs when a recommender system does not have enough information to make recommendations for a new user or item. There are two main types of cold start problems:
               -  User cold start: This occurs when a new user signs up for a service and the recommender system does not have any information about their past behavior.
               -  Item cold start: This occurs when a new item is added to a service and the recommender system does not have any information about how other users have rated it.
              
          -  The cold start problem refers to the challenge of making recommendations for new users or items that have little or no interaction data. There are several approaches to addressing this problem:
             -  Rank-based recommendations: For new users, you can recommend popular items based on their overall popularity or average rating. This approach doesn’t require any information about the user’s preferences and can help introduce them to popular items on the platform.
             -  Content-based filtering: For new items, you can use content-based filtering to make recommendations based on the item’s attributes or metadata. This approach doesn’t require any interaction data and can help introduce new items to users with similar preferences.
  
  -  Outputs -

      -  Recommend top 5 products with 50/100 minimum ratings/interactions.
  
  -  Approach -

      - Calculate average rating for each product.
      - Calculate total number of ratings for each product.
      - Create a DataFrame using these values and sort it by average.
      - Write a function to get 'n' top products with specified minimum number of interactions.

- Similarity based Collaborative filtering
  -  Objective
    
      -  Provide personalized and relevant recommendations to users.
  -  Outputs
    
      -  Recommend top 5 products based on interactions of similar users.
  -  Approach -

      -  Here, user_id is of object, for our convenience we convert it to value of 0 to 1539(integer type).
      -  We write a function to find similar users -
          -  Find the similarity score of the desired user with each user in the interaction matrix using cosine_similarity and append to an empty list and sort it.
          -  extract the similar user and similarity scores from the sorted list
          -  remove original user and its similarity score and return the rest.
      -  We write a function to recommend users -
          -  Call the previous similar users function to get the similar users for the desired user_id.
          -  Find prod_ids with which the original user has interacted -> observed_interactions
          -  For each similar user Find 'n' products with which the similar user has interacted with but not the actual user.
          -  return the specified number of products.
