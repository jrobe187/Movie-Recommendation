# Movie-Recommendation
Introduction	
Movie recommendations are important for any app storing movie data because it can show users what other movies they might like while factoring in the ones they already like. User-based approach finds other users similar to the input user and recommends movies that they liked to the input user. Item-based finds items similar to the items that the user liked and recommends these. Random walks identifies items that are similar to the input item and highlights a neighborhood of items similar to the input, any items from this neighborhood are then recommended.

Dataset
	The dataset used had 943 users, 1681 movies, and 100,000 ratings. We used the features movie_id, user_id, rating, and title. For preprocessing I dropped all missing values and converted all rating timestamps to readable dates.

Methodology
	For user-based we create a matrix of the cosine similarity for each pair of users based on their ratings. For item-based we define similarity between movies as the cosine similarity between ratings given by users for each movie. In random walk-based similarity is defined as nodes that are frequently visited when starting from the start node.

Implementation
	For user-based recommendations I get a list of all users above 0.5 cosine similarity, I then take the average rating of all movies for these users. I then recommend these in the order of descending average rating.
	For item-based I get the cosine similarity between the input movie and all other movies then sort by descending cosine similarity. The movie at the top is the most recommended.
	For random-walk based a graph is constructed connecting users to movies that they have rated and movies to users that have rated them. Random walks are done from the start node then a random node is chosen to move to. This is repeated walk_length times and the nodes most frequently visited are recommended.














Results and Evaluation
Item-Based seems to be the most effective in my opinion. From trying different movies I saw movies in the recommended list that were somewhat similar. I think Random Walk-based can be the most effective but it is needed to factor in edge weights based on user ratings.


Conclusion
	After this project I have a deeper understanding of how random walks with graphs work. I understand now that nodes that are similar to each other will have connections to each other and these nodes will be the most visited since they are the most connected to each other. This random walk serves to highlight a neighborhood of similar nodes. I already had an understanding for user-based and item-based that cosine similarity, or any other distance method, was used to define similarity for recommendations.
	To improve this I could edge weights to the random walk algorithm. These algorithms can be used in websites that harbor movie data like imdb or lettrboxd. These algorithms really could be used on any website that has user accounts and offers interactable items. These algorithms can give users personalized recommendations based on their account interaction history.
