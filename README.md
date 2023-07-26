# Telegram chat analysis    
#### made by [@pelmeshek1706](https://telegram.me/pelmeshek1706)

# **DISCLAIMER: All posts are fictitious and the real names of the participants do not match the names given. The messages contain foul language. This work was carried out with the aim of gaining experience with a certain type of speech**

The analysis was conducted on a specific dataset that contains foul language and possibly incorrect statements.

 All used libraries:
- <code>numpy</code>
- <code>pandas</code>
- <code>matplotlib</code>
- <code>sklearn</code>
- <code>time</code>
- <code>nltk</code>
- <code>plotly</code>
- <code>gensim</code>
- <code>tensorflow</code>
- <code>transformers</code>


### Analyzing the chat

First, let's take a look at the chat spammers

![msgs_users](https://github.com/Pelmeshek1706/telegram-chat-analyse/assets/94761102/1114529f-6262-4161-bbb5-9478a684e0eb)



and the activity graphs by day 
![msgs_per_day](https://github.com/Pelmeshek1706/telegram-chat-analyse/assets/94761102/e56852e1-8d8a-4e05-9da1-0165c6965ceb)

Also the activity of each user during certain hours 
![msgs_hour_users](https://github.com/Pelmeshek1706/telegram-chat-analyse/assets/94761102/b44b025b-3894-4854-ad25-bba94d40db86)


### Mood analysis models

In order to build a model to assess the mood of messages I applied the model from the haggling face website - [rubert-tiny2-russian-sentiment](https://huggingface.co/seara/rubert-tiny2-russian-sentiment?text=I+like+you.+I+love+you)
I applied it to the text that users were writing and got one of three labels -  *positive, neutral, negative*

after that I built a simple model for sentiment classification, you can see the results below 

#### Model evaluation
![model_evaluation](https://github.com/Pelmeshek1706/telegram-chat-analyse/assets/94761102/c9f3859e-e353-44cd-be9f-9baad78476ba)

The model is not perfect and is bumped to a certain figure which may be due to lack of data or poor partitioning as the lion's share of the data is labeled as *neutral*

Similarly, I chose the best model among the conventional machine learning models in the form of XGBoost. 

|XGBoost| precision | recall  | f1-score |  support |
|-------|-----------|---------|----------|---------|
|negative|       0.83|      0.36 |     0.50  |      53|
|  neutral |      0.82 |     0.97  |    0.89 |      257|
| positive  |     0.20  |    0.08 |     0.11  |      25|
| accuracy |           |           |    0.81 |      335|
| macro avg  |     0.62  |    0.47  |    0.50 |      335|
|weighted avg  |     0.78  |    0.81   |   0.77 |      335|


