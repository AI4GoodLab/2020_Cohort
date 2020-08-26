![logo](https://github.com/AI4GoodLab/2020_Cohort/blob/master/NewsworthyML/images/newsworthy.png)

# newsworthy.ml

## Table of Contents
- About the Project
- Live Demo
- Dataset
- Pipeline
- Models
  - Non-negative matrix factorization
  - Support vector machine
- Contact
- Acknowledgements


## About the Project

[newsworthy.ml](http://newsworthy.ml) is a platform that improves and informs a user's news-reading experience, by shining a spotlight on the imbalanced coverage of current events in today's media. 

The web app consists of two features: a map and an analytics dashboard. The map displays a range of news topics in the form of colored bubbles. Each bubble represents a set of stories that are of a certain news topic and category. The bubble is sized depending on its relative amount of coverage in the media. 

The analytics dashboard displays data about each user’s news-reading behavior. Through a browser extension, the app tracks the articles a user reads and the time spent reading each day. The data is then visualized through graphs in a personalized user dashboard. 

As a team, our primary goal is to empower readers to take control of their own information literacy.

## Live Demo

Our live demo can be found on [newsworthy.ml](http://newsworthy.ml/).

For the first prototype, we focused on building functionalities for the map feature. We scraped news articles from 21 news outlets in Canada – mostly those based in the Metro-Vancouver area. We then used topic modelling to visualize these articles by topic, each of which are represented as bubbles on the map. We used scoring by frequency to represent the amount of coverage each topic gets, and this is demonstrated by the size of each topic bubble. Finally, the color of each bubble represents the news category it belongs to. 

While there is no interactive user dashboard component for this first iteration, a static demo can be seen by clicking the ‘Dashboard’ button on the top right corner of the app.

We are currently in the process of iterating on the map prototype, as well as building out functionalities for the user dashboard. If you have any feedback, please don’t hesitate to reach out to our team!


## Dataset
We scraped 4206 news articles from 21 news outlets in Canada. Below you’ll find the breakdown of articles we pulled from each respective outlet. 

![article by outlet](https://github.com/AI4GoodLab/2020_Cohort/blob/master/NewsworthyML/images/articles_by_outlet.png)

These articles we used were also sampled from a range of news categories. Below you’ll find the breakdown of news articles by category. 

![article by category](https://github.com/AI4GoodLab/2020_Cohort/blob/master/NewsworthyML/images/articles_by_cat.png)



## Pipeline
Below is our workflow and ML pipeline. More on NMF and SVMs to follow.

![pipeline](https://github.com/AI4GoodLab/2020_Cohort/blob/master/NewsworthyML/images/pipeline.png)


## Models


### Non-Negative Matrix Factorization 
To generate topics from the articles we scraped, we used an unsupervised technique called Non-Negative Matrix Factorization (NMF). NMF involves the factorization of the data matrix A – which is made up of each articles’ text – into two more matrices, W and H, where none of these three matrices have any negative entries. W and H represent the topics found and the weights of those topics, respectively. The initial values of W and H are modified such that their product approximates A. 

#### Model
We used two different libraries to implement NMF in our project. To determine the optimal number of topics, we used the **gensim model** because it was compatible with the gensim Coherence Model. The coherence of the models was the metric we used to choose the optimal number of topics. We then used **sklearn** to extract the topics from our dataset and sort the articles into their respective topics. 

#### Input
For each news article data point, we used the following attributes: 
- The outlet
- Url
- Headline
- Authors
- Publish date
- Article text content 

#### Output
- Article topic number
- he words that make up the topic
- Residual score (metric of how well the topic approximates the data)
- The number of articles for that topic

Additionally, for each topic, the script outputs
- The words that make up the topic
- The number of articles for that topic
- Average residual score

Here’s an example of two of the topics that were generated and certain articles associated with them:

![topic 17](https://github.com/AI4GoodLab/2020_Cohort/blob/master/NewsworthyML/images/topic_17.png?s=100)


|     |     |
| --- | --- |
| [‘Grocers defend pandemic pay cut decisions as independently made despite emails, calls’](https://www.tricitynews.com/covid-19/grocers-defend-pandemic-pay-cut-decisions-as-independently-made-despite-emails-calls-1.24168500) | Tricity News |
| [‘Conservative leadership race enters final push’](https://www.ctvnews.ca/politics/conservative-leadership-race-enters-final-push-1.4830847) | CTV News |
| [‘It’s time for Canada to play hardball with China – and the United States’](https://www.therecord.com/ts/politics/political-opinion/2020/07/13/its-time-for-canada-to-play-hardball-with-china-and-the-united-states.html) | The Record |

![topic 13](https://github.com/AI4GoodLab/2020_Cohort/blob/master/NewsworthyML/images/topic_13.png?s=100) 

|     |     |
| --- | --- |
| [‘Fashion face-ward: Calgary designers create some stylish PPE’](https://calgary.ctvnews.ca/fashion-face-ward-calgary-designers-create-some-stylish-ppe-1.5026059) | CTV News |
| [‘Metrolinx changes course, makes masks mandatory on GO Transit vehicles starting Tuesday’](https://www.thestar.com/news/gta/2020/07/17/masks-will-be-mandatory-on-go-transit-vehicles-starting-tuesday.html) | The Star |
| [‘Surrey student makes hundreds of face masks, donates $2700 to local hospitals’](https://www.northdeltareporter.com/community/surrey-student-makes-hundreds-of-face-masks-donates-2700-to-local-hospitals/) | North Delta Reporter |



### Support Vector Machine

To classify the topics into one of **ten** preset news categories, we used a supervised model called Support Vector Machine (SVM). Our categories were as follows:
- COVID-19
- Business
- Politics
- Arts and entertainment
- Sports
- Health
- Science and technology
- Lifestyle
- Local
- Crisis updates 


#### Model
We used **sklearn** to create the SVM, and we trained it on labelled data of ~1,700 articles.

#### Input
The topic words generated by the NMF model (25 topics in total).

#### Output
- The category for each topic
- Probability that the topic belonged to its category


## Contact
**Official email:** newsworthy@gmail.com

### Team 
- Janna Agustin - https://github.com/jannalouisea - https://www.linkedin.com/in/janna-agustin/
- Jodi Boone - https://www.linkedin.com/in/jodi-boone-a9a989149/
- Harpriya Bagri - https://github.com/harpriyabagri - https://www.linkedin.com/in/harpriya/ 
- Miya Keilin - https://github.com/miyakeilin - https://www.linkedin.com/in/miyakeilin/
- Raveen Sidhu - https://www.linkedin.com/in/raveen-sidhu-366a5416b/ - https://github.com/raveensidhu




## Acknowledgement
- Aayushi Kulshrestha
- Francis Duplessis
- Linda Petrini




