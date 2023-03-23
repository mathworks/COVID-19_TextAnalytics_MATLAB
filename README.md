# **Understanding COVID-19 from Research Articles using Text Analytics in MATLAB**
[COVID-19 Open Research Dataset (CORD-19)](https://allenai.org/data/cord-19), offered by Allen Institute for AI and other leading research groups, is a collection of  thousands of articles related to COVID-19 and related coronaviruses. Here, we are using text analytics techniques in MATLAB to explore the articles and use topic modeling and document summarization to answer some of the relevant questions.

## **Overview**

***Goal***: Explore relevant articles to understand “what do we know about transmission?”

***Data used***: comm_use_subset from the dataset hosted at [COVID-19 Open Research Dataset (CORD-19)](https://allenai.org/data/cord-19)

***Techniques used***: Topic modeling and Document Summarization

***MATLAB Live Script***: TopicModel_Transmission_comm_use.mlx

![Wordcloud of Titles](/images/Wordcloud_Titles.png)


## **Steps**

**Step 1**:
First, we use a latent Dirichlet allocation (LDA) method to perform topic modeling to discover underlying topics in the articles. We test [four different solvers](https://www.mathworks.com/help/textanalytics/ref/fitlda.html#d120e1505):
* ‘cgs’: collapsed Gibbs sampling
* ‘avb’: approximate variational Bayes
* ‘cvb0’: variational Bayes, zeroth order
* ‘savb’: stochastic approximate variational Bayes

![Validation Perplexity for Solvers](/images/VPSolvers.png)


**Step 2**: After choosing a solver, we then choose the optimum number of topics by comparing validation perplexities for different numbers of topics.

![Validation Perplexity for Number of Topics](/images/VPTopics.png)

**Step 3**: Build the final model using the chosen solver and optimum number of topics. 

![Final Model Sample Topics](/images/wordcloud_6Topics.png)

**Step 4**: In order to answer the question “what do we know about transmission?”, we choose the most relevant article by identifying the topic with the word, “transmission”, having highest probability and then identifying the document in that topic that has the highest probability.

![Validatin Perplexity for Solvers](/images/RelevantAbstract.png)

**Step 5**: An alternate approach is to summarize the top abstracts.

**Next Steps**

There are many ways to dig deeper into this single question. Some of the possible approaches are:
* Use of ngrams (2 or more words) in topic modeling ([Analyze Text Data with Multiword Phrases](https://www.mathworks.com/help/textanalytics/ug/analyze-text-data-using-multi-word-phrases.html)),
* Use of TFIDF for topic modeling ([TFIDF](https://www.mathworks.com/help/textanalytics/ref/bagofwords.tfidf.html)),
* Extract summary with a query (such as transmission) using Maximal Marginal Relevance (MMR) algorithm ([mmrScores](https://www.mathworks.com/help/textanalytics/ref/mmrscores.html)), and
* Perform correlation analysis to find words most commonly associated to transmission ([Co-occurrence Analysis and Visualization](https://www.mathworks.com/matlabcentral/fileexchange/74776-co-occurrenceanalysis-and-visualization)).

## **Summary**
The aim of this example is to show
* how to use text analytics techniques to explore text data and build predictive models, and
* provide a starting point for researchers to build on it and dive deeper into unanswered questions regarding this pandemic. 

## **For more information on Text Analytics using MATLAB:**
* [Download a free trial](https://www.mathworks.com/campaigns/products/trials.html?prodcode=TA)
* Visit [Text Analytics Toolbox](https://www.mathworks.com/products/text-analytics.html)

### **Requires**

- [MATLAB R2020a](https://www.mathworks.com/products/matlab.html)
- [Text Analytics Toolbox](https://www.mathworks.com/products/text-analytics.html)
- [Statistics and Machine Learning Toolbox](https://www.mathworks.com/products/statistics.html)

[![View COVID-19_TextAnalytics_MATLAB on File Exchange](https://www.mathworks.com/matlabcentral/images/matlab-file-exchange.svg)](https://www.mathworks.com/matlabcentral/fileexchange/74942-covid-19_textanalytics_matlab)


Copyright 2020 - 2020 The MathWorks, Inc.


