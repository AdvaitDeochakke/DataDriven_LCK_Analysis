The project is summarized here

# Overall Description
Data from LCK players is taken, used to train a model. The model is an ensemble model which incorporates 
Neural Networks and traditional ML models.

The exact models used are LSTMs, Convolution networks, a stacked LSTM with dropout layers, and simple RNN. 
For traditional ML models, we have XGRegressor, Support Vectors, KNN regressors, GaussianProcess kernels, and 
a Random Forest regression model.

We use the models to generate points for players, these points are representative of their skill/otherwise value. It is based on the MVP points awarded to players by expert analysis.

Finally, we use such points to rank players within their roles. We use a second method of deciding ranks based purely on what the rank of the player is when sorting by a specific value. We aggregate these along with the base MVP point-rankings to get a final result.

We then show that our model gets 11 out of the 15 players which make up the top-3 rankings in expert based methods (All-Pro First to Third Teams from LCK Spring 2023), 2 out of 15 are a close 4th, while the other 2 are 5th and 6th in our ranking respectively.

We thus show that our model is well suited to predicting the best players across a split, but some unaccountable [by out model] conditions such as being overshadowed through overlapping stats (DMG%, GOLD% are shared across all 'carry' roles of ADC, Top, Mid), being unable to account for factors such as LIDERship or effect on team atmosphere, or strategizing skills can also greatly influence a player's ranking.(https://www.reddit.com/r/leagueoflegends/comments/11ckymg/hunis_thoughts_on_fakers_leadership_role_in_t1/)

# In-Depth Explanation for each part
## Data Acquisition and Pre-processing
As the Riot-API does not support pro-games, we use the private API data (stuff that is officially posted) and is available through sites such as Oracle's Elixir. This site gives us the data for players across the split, and we combine it with the MVP rankings availble on liquidpedia (or lol.fandom). This gives us the first stage of our data.

We take care of things such as team names, players who swap roles, etc.

Then we scale the data. The scaling is done per split. This is done with the logic of patches causing change in playstyle, gameplay, and more; so we shouldnt treat player data from 2015 on the same wavelength as player data from 2022. 

Furthermore, we keep a copy of the unscaled data, to record changes in model fit and performance with the two sets.

## Short note
We first check if there are very significant difference between players of a given role. The idea is that aggressive/defensive, tank/carry tops, or other various archetypes associated with players can be clearly seen through data. 

However, we find that when we run KNN Clustering on the role data, the silhouette scores obtained are always around ~0.3, which means that the clusters are not significantly different from each other. Thus we were unable to use data to clearly markdown different playstyles withing a given role.

## Feature selection and verifying difference between roles
We decided to rank players/develop different models for each role, and took a series of tests to verify that there is enough significant difference between roles (Based on their datapoints) to justify using different models. Plus, we also ran feature selection for each role based on RFE and VIF

We use scatterplot based on PCAs 1 and 2of the data, to see if we can visually see a clear difference between roles, and find Support and Jungle being extremely clearly differentiated from the rest, while Top, Middle, and ADC are also recognizable offset from each other but have decent overlap.

We then use an XGBClassifier and a LSTM model to check if we can reliably assign a role to player based on their datapoints. We get an accuracy of ~80% and ~75% for them respectively, and thus are able to say that yes, the roles have significant difference between them.

Next, we move to feature selection. We first get a correlation plot to visually check out our available features. When some features have insanely high correlation (for ex. greater than 0.9) we can take the inititative of removing them to prevent inflation.

We then run RFE on the data for each role, and get a list of representative columns. These supports help us to minimize noise in the dataset.


## Models
We use three main divisions of model, whose performance we evalute with the loss function of mean squared error, and a secondary evaluation with MAPE and R2_score 

### Neural Networks
We use a total of 5 models for checking performance. A basic LSTM with a linear activation function, a basic LSTM with sigmoid activation function, a stacked LSTM with Dropout layer, a Convolution, and simple RNN. 
We train a version of each based on the role data, for a total of 25 such models. For each neural network, we plot and see how our prediction corresponds to the actual MVP 'ranking'. 

We see that our neural networks are typically extremely poor in evaluating Top and Support players, while being ~okay for the other roles.

### Traditional ML Models
We use XGRegressor, RF, SVR, KNN, and GPK here. They are executed similarly to above, and we find that they are typically performing similar to our NN models. 

They have lower MAPEs, a bit higher MSE (loss), and similar or better R2 score. Especially in the Top and Support roles, our ML models seems to perform significantly better in accordance with expert rankings.

### Why we dont care about the actual number output
Our final goal is ranking players within their role, not giving a prediction of MVP points. We have a good model as long as our final rankings are good.

Another point is that some models are better at ranking certain roles compared to others, so we desire a collection of models to capture the various aspects involved. 

### Third and Final, Ensemble Model
We create a VotingRegressor to combine our Traditional ML model. To incorporate our Keras Neural Networks, we pass the outputs from the networks as a form of feature along with the other selected features. We thus augment the dataset and send them to the Voting Regressor to get a final output. 

## Rankings
We use a threefold system to arrive onto the final rankings for our players. We incorporate our model's rankings, rankings based on the percentile for players under their selected features, and the expert selected list.

First, we take the ranks based on the expert ratings (MVP Points). Its just simply sorting by MVP Points within the role, and then assignning ranks.

Next, we take the percentile ranks. We define these as the average of the ranks for the given player compared to their peers, for the selected features of their role. After taking the average, we sort and convert it to a true ranking.

Finally, we use our ensemble model to get an output of 'MVP points', which we utilize in the same manner as the first ranking scheme.

Lastly, we combine them, average, and convert to a true ranking.

## Results
To validate our model and rankings, we use the LCK All-Pro Teams as a form of checking the Top 3 players under each role. For our purposes, we use the full data from 2015-2022 LCK in the training process, and will now use data from LCK 2023 Spring to test our model. 

The All-Pro Teams selection process involves voting by a panel of industry experts, media representatives, and fans to identify the top-performing players in various positions over the course of the Spring Split season.

    MVP : Keria , Player of the Split : Keria

    First All Pro-Team : Zeus, Oner, Faker, Gumayusi, Keria

    Second All Pro-Team : Kiin, Peanut, Chovy, Deft, Kellin

    Third All Pro-Team : Doran, Canyon, Bdd, Peyz, Lehends

For our rankings, we create the following teams :

    First All Pro-Team (Model) : Kiin, Oner, Chovy, Viper, Keria

    Second All Pro-Team (Model) : Doran, Peanut, ShowMaker, Deft, Kael

    Third All Pro-Team (Model) : DuDu, Canyon, Faker, Peyz, Kellin

We can see an overlap of the following players within the top 3 for each role :
    
    Top : Kiin, Doran 

(Zeus is 4th in our rankings, DuDu is taken instead as third, pushing the other two one place higher)

    Jungle : Oner, Peanut, Canyon

(Interestingly, the exact order of rankings is also maintained)

    Middle : Chovy, Faker

(Their rankings are inverted, and Bdd is replaced with ShowMaker. Again, Bdd makes a close 4th on our list)

    Bottom : Deft, Peyz

(Both maintain 2nd and 3rd spot, but the first spot is replaced with Viper. Surprisingly, Gumayusi is a far 6th place on our list. This may be the result of nuances or other factors that our model does not account for)

    Support : Keria, Kellin

(Lehends appears 5th on our list, and Kael pushes into the top 3 instead)

Overall, there are many interesting factoids and things of note from this split, the key one I wish to mention is that the team 'T1', are just straight up the First All-Pro Team (All members of T1 are directly part of the First All Pro-Team). Coming from a close 3-2 defeat in a Best of 5 game at the 2022 Worlds', T1 have appeared equally stellar for the Spring 2023 split and sweeped the competition with a 17-1 W/L record in the LCK's double round robin format. 

This may be a possible cause of why T1 players are extremely highly ranked by experts, while our model which only looks at raw stats is not able to find much of a difference.

### Possible Explanation for model deficits
We thus show that our model is well suited to predicting the best players across a split, but some unaccountable [by out model] conditions such as being overshadowed through overlapping stats (DMG%, GOLD% are shared across all 'carry' roles of ADC, Top, Mid), being unable to account for factors such as LIDERship or effect on team atmosphere, or strategizing skills can also greatly influence a player's ranking. (Eg. Huni - ex-pro player, saying how Faker called plays minutes in advance and set up the team for success)

Other possible explanations for why our model rankings might differ from expert's All-Pro Teams could include differences in the weighting of different performance metrics or the inclusion of certain metrics that are not considered by the All-Pro Teams panel. Additionally, the model may not be able to account for intangible factors such as player experience, mentality, or team chemistry. Finally, the model may be affected by the quality of the data used to train it, such as differences in data collection or availability.

### TO ADD : MODEL ISSUES (IN ipynb not converted to readme yet)