The project is summarized here

# Overall Description
This project aims to create a predictive model for ranking professional League of Legends players in the Korean league (LCK) based on their in-game statistics. We use a combination of machine learning algorithms and statistical analysis techniques to identify the most important performance metrics and build a predictive model that can accurately rank players based on their role. Our model incorporates various features such as kill participation, gold per minute, damage dealt, and vision score, among others. 

We also take into account expert opinions and percentile rankings based on the performance of other players in each role. To validate our model, we compare its rankings with the All-Pro Teams selected by a panel of experts, media representatives, and fans. 

Our findings indicate that our model is effective in predicting the top-performing players within a split. However, it is limited in its ability to consider intangible factors such as team dynamics, mental state, and strategic decision-making. Despite this, our model can still be a valuable resource for teams, coaches, and fans to evaluate player performance and make informed decisions.

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
Our model is divided into three main categories: Neural Networks, Traditional ML Models, and an Ensemble Model. To evaluate the performance of these models, we use the mean squared error loss function, along with secondary evaluations using MAPE and R2_score.

### Neural Networks
For our Neural Networks, we use a total of five models, including a basic LSTM with a linear activation function, a basic LSTM with sigmoid activation function, a stacked LSTM with a Dropout layer, a Convolution, and a simple RNN. We train a version of each based on role data, resulting in a total of 25 models. For each neural network, we plot and analyze how our prediction corresponds to the actual MVP ranking. However, we find that our neural networks are not as effective in evaluating Top and Support players as they are for other roles.

### Traditional ML Models
In addition to our Neural Networks, we also employ Traditional ML Models, including XGRegressor, RF, SVR, KNN, and GPK. These models are executed in a similar manner to the neural networks, and we find that they typically perform similarly to our NN models. They have lower MAPEs, slightly higher MSE (loss), and similar or better R2 score. Interestingly, our ML models seem to perform significantly better in ranking Top and Support roles, in accordance with expert rankings.

### Why we dont care about the actual number output
Our final goal is to rank players within their role, rather than predicting MVP points. Therefore, the actual number output from the models is not a major concern. We believe our models are effective as long as the final rankings are accurate. 

### Third and Final, Ensemble Model
Finally, we create an Ensemble Model using a VotingRegressor to combine our Traditional ML models. To incorporate our Keras Neural Networks, we pass the outputs from the networks as a feature along with the other selected features. By augmenting the dataset in this manner, we can send the combined features to the Voting Regressor to obtain a final output.

## Rankings
Rankings are determined using a threefold system. First, expert ratings (MVP Points) are used to assign ranks within each role. Next, percentile ranks are calculated by comparing a player's rank to their peers for selected features of their role. The ensemble model is used to calculate MVP points, which are used to assign a third set of ranks. Finally, the three sets of ranks are combined, averaged, and converted into a final true ranking.

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

Overall, it is worth noting that all players from team 'T1' are part of the First All-Pro Team (expert), which is an unprecendented feat. There may be many reasons why the rankins differ between our model and experts, as we discuss below.

### Possible Explanation for model deficits
While our model is well-suited to predicting the best players across a split, there are several factors that it cannot account for, such as overlapping stats across different roles, intangible factors such as player experience or team chemistry, and the quality of the data used to train it. It is possible that the All-Pro Teams panel weights performance metrics differently or includes metrics that are not considered by our model.

Furthermore, it is worth noting that factors such as a player's effect on team atmosphere, strategizing skills, and leadership qualities can greatly influence their ranking, but may not be accounted for by our model. For example, ex-pro player Huni mentioned how Faker's ability to call plays minutes in advance and set up the team for success had a significant impact on their performance.

### Model Issues
Possible Issues with the model : 

1. Availability of stats : Not all stats our model chose [from the training dataset] may be available for any arbitrary testing dataset. For example, datasets from the LPL do not include stats like FB% (First Blood %age), CSD10 (CS Difference @10), etc.

2. All features are model selected : The issue here lies in explaining why certain features are missing or absent for particular role rankings. Eg. conventionally, the Bottom role is not expected to be evaluated with the extensive use of features such as WPM, CWPM, or WCPM. Our model makes these selections to give a good measure of MVP points, but it may seem as unexplainable choices to observers and experts. 

3. Limited model adaptation : For inputs of neural networks to the ensemble model, we do not weight the outputs based on any loss function. Similarly for comparing models inside the VotingRegressor, we also simply give arbitrary weightings based on visual analysis.

4. No accounting for first pricks/priority picks/lane counterpicks : The game's structure means that teams generally have at most two carry champions, which are usually in the Bot and (Mid or Top) positions. This can negatively impact other positions, where they always get put on champions which have good econ but lower ceilings, or be put into counter matchups which negatively impact the stats which we consider. 

5. Not accounting for teamfight importance: Our dataset may skew towards stats like kills and gold%, which may not accurately represent the importance of tanks or champions with heavy CC in teamfights. This can result in the players which regularly play such champions being misrepresented in our model's rankings.

### Future Work:

1. The most important area of improvement for our model is to refine the way we process and use our models. Currently, we use a variety of models in an arbitrary manner with arbitrary weights. By refining this process, we can potentially see a significant boost in the accuracy of our MVP Points outputs, which would have a smaller effect on the player rankings themselves.

2. Improving our feature selection process can increase the adaptability of our model. We can create a list of features to be selected and in what order, allowing us to navigate around the lack of availability of certain features. Furthermore, we can apply weightings to the features so that the rankings received from more important features are worth more than those received from less important features.