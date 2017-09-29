# Machine Learning Email

Every email programs since the 1980s presents emails by ‘date received’. This is a mistake: only 15% of emails require us to reply or take some action (1). Emails should be presented by importance, with ones requiring action at the very top.

To create this, I use machine learning to classify emails and developed an iOS mail client. 

- 1st, I used Amazon Mechanical Turk to create a dataset of labeled (eg. action required or not) emails.
- 2nd, cleaned the data: resolved labeling conflicts, generated the final dataset.
- 3rd, generated a ML model by employing a succession of techniques: Count Vectorizer, TFIDF, Linear SVC, Random Forest, Naive Bayes. The key metric I optimized for was ‘recall rate’ for action required emails.
- 4th, integrated the ML model into a bespoke iOS email client to developed for the project.
 
(1) https://cs224d.stanford.edu/reports/EugeneLouis.pdf


# System Overview

<img width="800" src="https://user-images.githubusercontent.com/13486833/30995352-709083ca-a46e-11e7-80b6-f69564af1658.jpeg">

# Mechanical Turk:
Contributors were asked to label emails as “Action Required”, “Read Later” or “Neither”. They were given the following prompt “Your name is Sally Beck, these are your emails. You have to decide
1) if these emails ask you to perform some action, like replying or doing something in real life. Or
2) if the E-Mail can be read later. For example, it just contains general information.”

# Mechanical Truk Question Example

<img width="800" src="https://user-images.githubusercontent.com/13486833/30995570-04d3868a-a470-11e7-9fa8-fdceecb4c853.png">


# Dataset Generation

<img width="800" src="https://user-images.githubusercontent.com/13486833/30995348-6d682de2-a46e-11e7-9a41-920fc59e1d3e.jpeg">


# Cleaning
While lots of data cleaning can happen as a result of manipulating vectorizer parameters, there is one potentially important cleaning aspect for email datasets, people’s names. Unlike, say text messages, email correspondence is more akin to letter writing, with salutations and signatures. Rather than having over 7000 person names (of those, 600 are unique) in the word vector, we will remove all names and replace them with “propername”. Names in the body of emails are identified by the nltk names corpus of “male” and “female” names. In this version of the project, the focus is more on content of emails rather than names and potential networks of the individuals involved. Removing these 600 + names is also attractive from a dimensionality reduction standpoint.


# Creating the Model

The goal is to minimize the number of false positives for action, thus the key metric is "recall", we want to maximize it. LinearSVC modes had more consistent recall rates for Yes’s and No’s, both in the 70s While Random forest and NB had one recall score in the 60s with another in the 80s. the LinearSVC, with tfidf was selected because it was most consistent, with both recall rates of 75% Furthermore, iOS does not current support NB via sklearn, so it is only shown here for comparison.

<img width="800" src="https://user-images.githubusercontent.com/13486833/30995429-02273f54-a46f-11e7-8ff9-d6a37408895f.png">


