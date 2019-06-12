# Project aims

In recent years, the range of funding options for projects created by individuals and small companies has expanded considerably. In addition to savings, bank loans, friends & family funding and other traditional options, crowdfunding has become a popular and readily available alternative. Kickstarter, founded in 2009, is one particularly well-known and popular crowdfunding platform. It has an all-or-nothing funding model, whereby a project is only funded if it meets its goal amount; otherwise no money is given by backers to a project.

A huge variety of factors contribute to the success or failure of a project — in general, and also on Kickstarter. Some of these are able to be quantified or categorised, which allows for the construction of a model to attempt to predict whether a project will succeed or not. The aim of this project is to construct such a model and also to analyse Kickstarter project data more generally, in order to help potential project creators assess whether or not Kickstarter is a good funding option for them, and what their chances of success are.

My blog post about this project and its results was published in [Towards Data Science](https://towardsdatascience.com/using-machine-learning-to-predict-kickstarter-success-e371ab56a743?source=friends_link&sk=9d097ddca02077b38e09a59736e39ff8).

![](Kickstarter_prediction.png)
![](kickstarter-logo-color.png)

# Final model evaluation and interpretation
Each model was able to achieve an accuracy of 73-75% after parameter tuning. The final chosen model is a tuned XGBoost model, which had the highest test set weighted average F1 score of 0.747.

Interestingly, each model performed worse at predicting failures compared to successes, with a lower true negative rate than true positive rate. I.e. it classified quite a few failed projects as successes, but relatively few successful projects as failures. Possibly the factors that might cause a project to fail are more likely to be beyond the scope of the data, e.g. poor marketing, insufficient updates, or not replying to messages from potential backers.

The false positive and false negative rates mean that, if the data about a new project is fed through the model to make a prediction about its success or failure:
- if the project is going to end up being a success, the model will correctly predict this as a success about 80% of the time
- if the project is going to end up being a failure, the model will only correctly predict this as a failure about 65% of the time, and the rest of the time will incorrectly predict it as a success


# Recommendations
Some of the factors that had a positive effect on success rate and/or the amount of money received (as deduced from a mixture of data exploration and model feature importances) are:

Most important:
- Smaller project goals
- Being chosen as a staff pick (a measure of quality)
- Shorter campaigns
- Taking longer between creation and launch
- Comics, dance and games projects

Less important:
- Projects from Hong Kong
- Film & video and music projects are popular categories on the site, and are fairly successful
- Launching on a Tuesday (although this is also the most common day to launch a project, so beware the competition)
- Launching in October
- Launching between 12pm and 2pm UTC (this is related to the country a project is launched from, but backers could come from all over the world)
- Name and blurb lengths (shorter blurbs and longer names are preferred)

Factors which had a negative effect on success rate and/or the amount of money received are:

Most important:
- Large goals
- Longer campaigns
- Food and journalism projects
- Projects from Italy

Less important:
- Launching on a weekend
- Launching in July or December
- Launching between 6pm and 4am UTC

Overall, Kickstarter is well suited to small, high-quality projects, particularly comics, dances and games. It is less suited to larger projects, particularly food and journalism projects.
