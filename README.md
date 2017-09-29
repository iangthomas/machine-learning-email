# Machine Learning Email

Every email programs since the 1980s presents emails by ‘date received’. This is a mistake: only 15% of emails require us to reply or take some action (1). Emails should be presented by importance, with ones requiring action at the very top.

To create this, I use machine learning to classify emails and developed an iOS mail client. 

- 1st, I used Amazon Mechanical Turk to create a dataset of labeled (eg. action required or not) emails.
- 2nd, cleaned the data: resolved labeling conflicts, generated the final dataset.
- 3rd, generated a ML model by employing a succession of techniques: Count Vectorizer, TFIDF, Linear SVC, Random Forest, Naive Bayes. The key metric I optimized for was ‘recall rate’ for action required emails.
- 4th, integrated the ML model into a bespoke iOS email client to developed for the project.
 
(1) https://cs224d.stanford.edu/reports/EugeneLouis.pdf


System Overview

<img width="800" src="https://user-images.githubusercontent.com/13486833/30995352-709083ca-a46e-11e7-80b6-f69564af1658.jpeg">
