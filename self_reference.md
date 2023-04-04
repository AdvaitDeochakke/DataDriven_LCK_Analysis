Abstract
   Objective of project 
   Methods used in your project 
   Outcome of project 
   Scope of project 
1. Introduction - explain the project details   
2.Review of literature (all papers related to work referred and written)
3.materials and methods
     3.1 Info about models—(algo/ pseudocodes)
     3.2 dataset
     3.3 architecture and explanation 
4. Proposed works
     4.1 novelty
     4.2 Project contributions 
      
5. Results and discussion 
   5.1 results
   5.2 figures, .comparisons tables,
   5.3 explanation 
6. Conclusion - quantify your results and explanation 
(github link should be provided for the respective project ) 
7. References

Abstract :
This project aims to develop a model that predicts the top-performing players in the League of Legends Champions Korea (LCK) based on statistical analysis. To accomplish this, we trained our model on the Spring and Summer split data from the 2015-2022 LCK seasons and tested it on data from the LCK 2023 Spring season. Our model's rankings were then compared to the All-Pro Teams selections, which are made by a panel of industry experts, media representatives, and fans. The outcome of our project is a list of the top three players in each role, as determined by our model. The scope of our project is limited to the LCK and the performance metrics we used in our model, which include factors such as damage dealt, gold earned, and kill participation. While our model provides a useful tool for predicting player performance, it is important to note that it does not account for intangible factors such as player experience, mentality, or team chemistry, which can also influence a player's ranking. Our model demonstrates a high degree of accuracy in predicting the top-performers, thus providing a valuable resource for coaches, teams, and fans to evaluate player performance.


Introduction :
<self reference>
I. Background and context
A. Overview of esports and the League of Legends (LoL) competitive scene
B. Importance of player performance evaluation and ranking in LoL esports
C. Current methods of player evaluation and ranking in LoL esports

The world of esports has exploded in recent years, with millions of fans tuning in to watch their favorite teams compete on the global stage. One of the most popular games in the esports world is League of Legends (LoL), a multiplayer online battle arena game developed and published by Riot Games. In LoL, players control a champion with unique abilities and battle against a team of other players to destroy the opposing team's nexus, a structure located in the enemy base. The game is played at a high level of competition, with professional players from around the world competing in organized leagues and tournaments for lucrative prizes and recognition.

Player performance evaluation and ranking are of utmost importance in LoL esports, as they provide valuable insights into a player's strengths and weaknesses and can help teams make informed decisions when selecting players for their rosters. The LoL community uses a variety of methods to evaluate and rank players, including statistics-based rankings, expert evaluations, and fan voting. These rankings are used to identify the top-performing players in the game, as well as to inform team management decisions, such as player trades and roster changes. Despite the importance of player ranking and evaluation, there is still much debate over the best methods to use and which factors should be considered in the evaluation process. This research paper aims to explore the current methods of player evaluation and ranking in LoL esports, and to propose new and innovative approaches that can improve the accuracy and usefulness of these rankings.


II. Project objective and methods
A. Objective of developing a statistical model for player evaluation and ranking in LoL esports
B. Methodology used for developing the model, including data sources, variables considered, and statistical techniques employed
C. Comparison of the model with other methods of player evaluation and ranking in LoL esports

Esports and the League of Legends (LoL) competitive scene have gained immense popularity over the years, making it a major segment in the gaming industry. The significance of player performance evaluation and ranking in LoL esports is crucial for the industry's growth and player recognition. Current methods of player evaluation and ranking in LoL esports are limited in their ability to provide an objective and statistically rigorous approach. Therefore, the objective of this project is to develop a statistical model for player evaluation and ranking in LoL esports.

To obtain the necessary data for our model, we utilized various sources, including the Riot-API and private API data from Oracle's Elixir, as the Riot-API does not support pro-games. We also incorporated MVP rankings from reputable sites such as liquipedia to enhance our data. To ensure accuracy, we adjusted for factors such as team names and player role-swaps.

We then proceeded to pre-process the data by scaling it per split, acknowledging that patches can cause changes in gameplay and playstyle that affect player performance. We kept an unscaled dataset to compare the performance of the two sets. We also performed data cleaning and normalization to ensure data consistency and accuracy.

To develop a robust and reliable statistical model, we will use a range of statistical techniques, including regression analysis and  neural networks. The model will consider various factors, including individual and team performance, game statistics, and other relevant factors. We will evaluate the effectiveness of the model by comparing it with existing methods of player evaluation and ranking in LoL esports.

The developed model will provide a more objective and statistically rigorous approach to player evaluation and ranking in LoL esports. This project's outcomes will contribute to enhancing the accuracy and reliability of player evaluation and ranking in the LoL esports scene. Moreover, the scope of this study will extend beyond LoL esports, as the developed model's approach and methodology can be applied to other esports games as well.


III. Project outcome and scope (maybe not needed, recheck later)
A. Results of the model in predicting top-performing players and creating All-Pro Teams in the LCK
B. Identification of factors that may affect player ranking and evaluation beyond the model's scope
C. Implications of the model for future research in LoL esports and player performance evaluation.


Extra Lit Reviews : :
https://www.scitepress.org/Papers/2022/108959/108959.pdf 
This is a summary of the webpage:

The webpage contains a research paper that proposes two performance metrics for modeling and predicting the outcome of e-sports matches in League of Legends, a popular MOBA game. The first metric is based on a machine learning approach that uses individual player variables of a match. The second metric is based on heuristics derived from the machine learning approach. The paper evaluates the second metric by applying it for winning prediction purposes and shows that it can predict the outcome of matches with 86% accuracy. The paper also evaluates the importance of different roles of a LoL team to the match outcome and finds that the influence of a particular role is negligible.

http://www.sbgames.org/sbgames2018/files/papers/ComputacaoShort/188226.pdf
This is a summary of the webpage:

The webpage contains a research paper that compares different recurrent neural networks in the task of predicting the result of a competitive match in League of Legends using information from a specific minute of the game. The paper shows that a simple RNN is the most effective network and achieves an accuracy of 63.91% when using data from minutes 0 to 5 and 83.54% when using data from minutes 20 to 25. The paper also argues that this kind of network can be used to identify the power spikes of different team compositions and win conditions.

https://search.proquest.com/openview/5d4456188150f0170efdc4ec70ba9dc0/1?pq-origsite=gscholar&cbl=18750&diss=y
or https://repository.charlotte.edu/islandora/object/etd:2482/datastream/PDF/download/citation.pdf
The response is derived from web search results. Here is a short summary of the paper and its key points:

- The paper aims to forecast the most valuable player (MVP) of the National Basketball Association (NBA) using machine learning methods.
- The paper uses data from 1980 to 2019 to train and test various models, such as logistic regression, random forest, and neural network.
- The paper evaluates the models based on accuracy, precision, recall, and F1-score, and compares them with human experts and media predictions.
- The paper finds that the neural network model outperforms the other models and the human experts in predicting the MVP.
- The paper also identifies the most important features for MVP prediction, such as points per game, win shares, player efficiency rating, and team wins.

https://ieeexplore.ieee.org/abstract/document/9065758/ 
The response is derived from web search results. Here is a short summary of the paper and its key points:

- The paper aims to predict the winner of a match in League of Legends (LoL), a popular multiplayer online battle arena (MOBA) game, using feature selection and ensemble methods.
- The paper uses data from 50,000 matches collected from Riot Games API, and extracts 57 features related to champion selection, team composition, and in-game statistics.
- The paper applies various feature selection methods, such as correlation-based feature selection (CFS), information gain (IG), and reliefF, to reduce the dimensionality and redundancy of the features.
- The paper also applies various ensemble methods, such as bagging, boosting, and stacking, to combine multiple base classifiers, such as decision tree, k-nearest neighbor, and support vector machine.
- The paper evaluates the performance of the models based on accuracy, precision, recall, and F1-score, and compares them with a baseline model that uses all features without feature selection or ensemble methods.
- The paper finds that the stacking model with CFS feature selection achieves the best performance with an accuracy of 86.8%, followed by the bagging model with IG feature selection with an accuracy of 86.6%.
- The paper also identifies the most important features for victory prediction, such as gold difference, kill difference, first inhibitor, first baron, and first dragon.

1) Application of Neural and Regression Models in Sports Results Prediction
(doi: 10.1016/j.sbspro.2014.02.249)
The results of the investigation into the group of 18 year olds javelin throwers
show that the created neural models offer much higher quality of prediction than
the nonlinear regression model (absolute network error 16.77 m versus absolute
regression error 29.45 m). The optimal set of variables that are the most
informative and so usable as the explanatory variables of the nonlinear
regression models and neural models consists of: cross step with assuming the
throwing stance, specific power of the arms and the trunk, specific power of the
abdominal muscles and grip power. The investigation’s results explicitly
demonstrate that neural models are a tool which is far superior and offers better
optimization possibilities in predicting sports results, athlete recruitment and
selection processes, than the widely applied regression models.

2) Intelligent sports prediction analysis system based on improved Gaussian fuzzy
algorithm (https://doi.org/10.1016/j.aej.2021.08.084)
In order to improve the effect of sports prediction analysis, this paper analyzes
the movement recognition of sports and analyzes the traditional high-speed
model. Moreover, on this basis, this paper proposes a reliable sports action
recognition algorithm, which can be used as the core algorithm for sports action
recognition. This paper mainly constructs a standard database structure, and
enters a reliable standardized action model in the database structure. Moreover,
this paper compares the identified sports action model with the standard action
model to determine the accuracy of the sports action.
In addition, this paper uses statistical analysis to study sports training and sports
competitions, and obtains prediction results through multi-factor analysis and
comparison. Finally, this paper uses experimental research to predict the
accuracy of sports action recognition and the effect of sports prediction analysis
on the system constructed in this paper. From the research results, we can see
that the model constructed in this paper has certain effects.

3) Predicting Sports Results with Artificial Intelligence – A Proposal Framework for
Soccer Games (doi: 10.1016/j.procs.2019.12.164 )
Artificial Intelligence is becoming more and more popular as the technology
evolves. With a properly data set and a specific technique for a sport’s choice it is
possible to achieve great accuracy predicting the outcome of a sport match, even
better than the domain experts. Based on the analysis of the related works, it was
proposed a model and feature selection for predicting soccer outcomes.
Furthermore, these systems can also be useful to make profit in betting
industries, using science on our side. As a future work, the knowledge reported
will serve as the base to create a predictive model for soccer matches. For this
assignment, computer science methods will be used as described in discussion to
get a relatively large amount of data input and features of several leagues and
seasons throughout the world and Artificial Intelligence techniques such ANN to
try to obtain a high accuracy model.

4) Prediction and Planning of Sports Competition Based on Deep Neural Network
(https://doi.org/10.1155/2022/1906580)
The establishment of the autoregressive summation model for predicting the
development of sports competition in China has undergone several
improvements, including the neural network prediction model of complex brain
structure and the improved network prediction model. The results of these
efforts have shown that the improved complex brain structure model prediction
has a remarkable impact on the accuracy of predictions. The neural network with
complex brain structure outperforms traditional regression models in predicting
sports competition results, as shown in comparison experiments. Running events
showed the most accurate predictions, while other events had poor results.
Furthermore, the improved neural network model was able to reduce the
prediction error by about twice as much as the original model, further solidifying
its effectiveness in predicting the results of sports competitions. In conclusion,
the establishment of the improved complex brain structure model has greatly
enhanced the accuracy of predictions in the field of sports competition
development in China.

5) Prediction of football match results with Machine Learning (doi:
10.1016/j.procs.2022.08.057 )
This article analyzes the development of models for predicting the outcomes of
football matches for sports betting. Two data sources were used, and the analysis
resulted in important conclusions about the variables used in the models. Several
algorithms were compared to create the best prediction model, which was
trained with data from four seasons and tested with all games from the
2016/2017 English Premier League season. The model correctly predicted 65.26%
of games, with a higher profit margin than previous case studies. Future plans
include integrating the forecast model into a decision support system to assess
the risk of bets and provide support for profit in sports betting.

6) Sports match prediction model for training and exercise using
attention-based LSTM network (https://doi.org/10.1016/j.dcan.2021.08.008)
The paper describes an attention-based sports-aware LSTM model (AS-LSTM) for
predicting sports match results. It uses the attention mechanism to assign
different weights to different historical game records and focuses on the team's
short-term game status through a sliding time window. The AS-LSTM model has
three steps in its design: (1) Basic LSTM model prediction, (2) Combination of
LSTM with attention mechanism to pay more attention to influential historical
competition results, (3) Use of sliding window to better extract the team's shortterm competition status. The data for the model was collected for nine months,
including goals, goals lost, ball possession rate, home-court advantage, match
time, and match results. However, the model is not perfect and still needs
improvement.

7) Mechanics and Metagame: Exploring Binary Expertise in League of Legends
(https://doi.org/10.1177/1555412015590063)
In League of Legends, expertise is divided into two categories: mechanical and
metagame. Mechanical expertise refers to in-game elements such as avatar
control and interface navigation. Metagame expertise involves the awareness
and ability to negotiate the game around the game, including the formulation of
new strategies and the analysis of data sets. Metagame expertise is deemed so
important in competitive play that toxic behavior can arise when a player lacks it.
The social conventions surrounding metagame expertise and the response to
unconventional play forms are areas that could be studied to understand the
attitudes of League of Legends players. The accumulation of both mechanical and
metagame expertise in League of Legends is also noteworthy and could be
studied in the context of a new player's progress within the metagame. The
difference between the metagames of team play and solo play is also an
interesting area of study as it reflects the influence of player communication on
the metagame. Metagame expertise is a crucial component of competitiveness in
not just League of Legends but other strategic multiplayer games as well.

8) Coordination, Communication, and Competition in eSports: A Comparative
Analysis of Teams in Two Action Games
(https://dl.eusset.eu/handle/20.500.12015/3122)
The study analyzed the main topics relevant to the field of CSCW (Computer
Supported Cooperative Work) in the context of two popular eSport games, CS:GO
and R6. The research showed that eSport teams, especially those playing action
games, can be considered a mix of action and knowledge-intensive teams. These
games are immersive and players identify with their virtual avatars, making them
virtual action teams. The results showed that the captain and coach are the most
important roles during matches, while managers have more responsibilities
before and after matches. Horizontal specialization was explored with different
roles available in each game. Players tend to change roles, which can improve
collective intelligence. Communication is an important factor for success and
players use different methods, including non-verbal communication, voice chat,
and text chat. Overall, the study highlights the importance of coordination and
communication in eSport teams and how CSCW can be applied to this field.

9) A data-driven approach to predicting the most valuable player in a game
(https://doi.org/10.1002/cmm4.1155)
The authors conducted experiments to analyze the results of three approaches
for evaluating player performance in handball: PCA, meta-heuristics (using PSO),
and a fuzzy method. The PCA approach gave reasonable results but had low
accuracy in identifying MVPs (65%). The meta-heuristic approach had better
accuracy in identifying MVPs (76%) but had difficulty in interpreting the weights
obtained. The fuzzy method was best in interpretability but had the worst
accuracy and MRR (rank). The results of all three approaches were not
satisfactory, leading to concern about the possibility of their application in a realworld context.

10) Ranking Practices and Distinction in League of Legends (DOI:
http://dx.doi.org/10.1145/2967934.2968078)
The study discussed the impact of ranking on player experience in League of
Legends (LoL). The study found that specific ranks were often mentioned when
players referred to other players, and this rank became a descriptor of the player.
Stereotypes were formed around different ranks, with players using ranks to
describe not only skill level but also other aspects such as in-game collaboration,
personality, and willingness to learn. Players often described their own ranks as
central to their experience and constructed narratives to emphasize their rank
history and the effort put into reaching a desired rank. The study also found that
higher ranks provided players a sense of achievement and self-esteem, with
some players playing hundreds or thousands of games to reach a desired rank.

