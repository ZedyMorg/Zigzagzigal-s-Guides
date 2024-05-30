# Data parsing on Steam API and steam community website

**The goal of this project is to collect data regarding the strenghts of each civilization from the guides on Civilization VI made by Zigzagzigal (a user on Steam).** 

## 1. "Victory Skew" score
**We first parsed the "Victory Skew" score for each civilization with a guide (The "Dataparsing on Guides.ipynd" file).**

  - The "Victory Skew" score is defined as such : "The civ is subjectively graded based on how much it leans towards a specific victory type - not how powerful it is. Scores of 3 or more mean the civ has at least a minor advantage towards the victory route."

After parsing all the guides for the information on victory skew, we created a dataframe (guides.csv) containing the name of the leaders, the civilizationit's played in, the score for each victory type, a new "flexibility score" (the mean of all scores for the same leader) and the link in which the guide can be found. 

We had to customize our "for" loop, since the data was not always consistent. Before an update (GS) there were only 4 possible victory type and the names were not always consistent.

## 2. Steam acheivements
**Once we had our "guides" dataset, we parsed throught Steam APIs to get information on acheivements related to having a win with the leaders (Scrape Steam acheivements info.ipynb file).**

To access Steam's API, a Steam API key is needed, and steam's policy is to keep that key personal, that is why we hid marked it as XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX in our public file. 

We first accessed all acheivements for a specific steam ID (In this case, me), then got information on thoses achievements to give them their names and descriptions as we see in the Steam application and filtered them for the specific acheivements "Win a game as" and "Win a regular game as".

We then joined our previous dataset "guides" with this new dataset while fixing inconsistencies on the names of some leaders to create our full dataset (guide_with_achievements.csv) in which we have the data regarding the completion of the acheivement or not.

## 3. Visualizing our results
**Our last step was to add a UI to make it easier to filter what kind of civilization the user wants to play based on the scores (Display files.ipynb).**

We also color coded the strongest scores, but unfortunately the Seaborn library is not showing in GitHub.

6 leaders at the end of our dataframe (Julius Caesar, Tokugawa, Yongle, Ludwig II, Theodora and Elizabeth I) have None values because there were no guides made for those yet. We still left them in our dataframe because it is still possible to get acheivements for those.
