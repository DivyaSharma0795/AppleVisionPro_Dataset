# Sentiment Analysis on Tweets about Apple Vision Pro

This project conducts a detailed sentiment analysis on tweets related to the Apple Vision Pro. This innovative product has significantly influenced AR experiences with its advanced features. The tweets were gathered from January 1, 2024, to March 16, 2024, a period that encompasses the product's launch and availability.

The Apple Vision Pro, launched on February 2, 2024, has revolutionized AR experiences with its advanced capabilities. It has been praised for its seamless integration of virtual elements into the real world, earning recognition as a game-changer in various industries, including design and gaming. The product has received widespread acclaim for its innovation and potential.

### Data Collection

Data was collected using Twitter's API with OAuth v2.0. This ensured that the tweets were filtered to include only those referencing the Apple Vision Pro. The dataset consists of 26,704 tweets collected during this period. The search terms used were the hashtag “#AppleVisionPro” and “Apple Vision Pro”. The data was subsequently uploaded to HuggingFace and is publicly accessible for analysis.

The Apple Vision Pro's US availability press release was on January 8, 2024 (indicated by the green line in the chart below) – this led to an increase in the number of tweets as well as a rise in Apple's stock prices.

![Tweets Over Time](03%20Resources/Tweets_Over_Time.png)

The product became available from February 2, 2024 (indicated by the red line in the chart below) – this also led to an increase in the number of tweets and a brief rise in the stock price.

![Tweets Over Time](03%20Resources/Price_Over_Time.png)


## Dataset Access

The dataset is available on the Hugging Face Datasets library under the name "divyasharma0795/AppleVisionPro_Tweets".
To access the dataset, use the following Python code:

```python
from datasets import load_dataset
dataset = load_dataset("divyasharma0795/AppleVisionPro_Tweets")
```


### Sentiment Analysis

Since the tweets were unlabelled, sentiment analysis needed to be performed to gather conclusions based on the data. The sentiment analysis was executed via four distinct methodologies:

-  `TextBlob`: A Python library tailored for processing textual data, offering a straightforward API for various natural language processing (NLP) tasks such as sentiment analysis. It uses a bag-of-words approach and calculates the polarity and subjectivity of sentences, which makes it fast but less accurate for complex sentences.

-  `VADER (Valence Aware Dictionary and sEntiment Reasoner)`: A lexicon and rule-based sentiment analysis tool finely attuned to sentiments expressed in social media. It uses a combination of qualitative and quantitative means to determine sentiment scores. It is particularly useful for handling social media text, yet it may fail to accurately interpret more complex, context-dependent sentiments.

-  `roBERTa`: A transformer-based model developed by Facebook's AI team, a variant of BERT finely optimized for NLP tasks. It uses a masked language model approach, which allows it to consider the full context of a sentence. It is highly accurate but requires more computational resources and time.

-  `distilBERT`: A lighter, faster, and more economical version of BERT crafted by Hugging Face, also a transformer-based model widely employed for NLP tasks, including sentiment analysis. It is a distilled version of BERT that retains most of the original model's performance while being more efficient, making it a good choice for real-time sentiment analysis.


### Results

The sentiment analysis outcomes are presented in a comparative format, facilitating a comprehensive grasp of the public sentiment towards the Apple Vision Pro within the specified timeframe. The performance of each model was evaluated based on its speed, interpretability, and context-awareness.

- **TextBlob Model**: This model, available with Python’s TextBlob library, is super fast, taking approximately 3 seconds to process 26,705 rows. It is useful for basic non-context based classification and is interpretable as the training dataset is available.

- **VADER Model**: This model, available on NLTK (“vader_lexicon”), is fast, taking approximately 30 seconds to process 26,705 rows. It is useful for basic non-context based classification and is interpretable as it is rule-based.

- **DistilBERT Model**: This model, available on HuggingFace (lxyuan/distilbert-base-multilingual-cased-sentiments-student), is slower, taking approximately 25 minutes to process 26,705 rows. It is useful for context-based classification but is non-interpretable due to its complexity.

- **RoBERTa Model**: This model, available on HuggingFace (cardiffnlp/twitter-roberta-base-sentiment-latest), is the slowest, taking approximately 40 minutes to process 26,705 rows. It is useful for context-based classification but is non-interpretable due to its complexity.

The following charts provide a visual representation of the sentiment analysis outcomes:

![Polarity By Model](03%20Resources/Polarity_By_Model.png)
![Polarity Over Time](03%20Resources/Polarity_Over_Time.png)
![Polarity Share Over Time](03%20Resources/Polarity_Share_Over_Time.png)

### Performance Evaluation

Each sentiment analysis model was evaluated based on the following criteria:

- **Accuracy on New Data**: The models were tested on a controlled dataset of dummy tweets generated using large language models like ChatGPT. These tweets were tagged as positive, negative, or neutral, providing a benchmark for assessing the model's performance.

- **Interpretability**: The ability of the marketing team to understand and act upon the model's outputs was considered. This includes the transparency and explainability of the model's decision-making process. For instance, rule-based models like `TextBlob` and `VADER` are more interpretable than complex transformer-based models like `DistilBERT` and `RoBERTa`.

- **Efficiency**: The processing time and computational resources required by each model were evaluated. This is crucial for assessing the practicality of deploying each model in terms of scalability and real-time performance. For example, while `DistilBERT` and `RoBERTa` provide more nuanced sentiment analysis, they are slower and require more computational resources than `TextBlob` and `VADER`.

The evaluation results were used to guide the conclusion and recommendation of the best model for this project.


### Conclusion

The sentiment analysis models used in this project each have their strengths and weaknesses. 

- `TextBlob` and `VADER` are fast and provide basic, non-context-based sentiment classification. They are useful for answering questions like: "Is this tweet generally positive or negative?" However, they may not capture the nuances of sentiment in complex or context-dependent statements.

- `DistilBERT` and `RoBERTa` provide more nuanced, context-aware sentiment analysis. They can answer questions like: "How positive or negative is the sentiment expressed in this tweet, and what are the underlying reasons?" However, these models are slower and require more computational resources.

Considering the balance between speed, accuracy, and context-awareness, `DistilBERT` stands out as the best choice for this project:

- It classifies more tweets as positive or negative, instead of labeling them as neutral.
- It provides more meaningful and actionable insights compared to simpler models.
- It is relatively fast, taking around 25 minutes to analyze 26,705 tweets.
- It offers more context-aware and accurate sentiment analysis than simpler models, despite being less interpretable than rule-based approaches.

`RoBERTa` also provides accurate and contextual sentiment analysis, but its slower processing time (around 40 minutes for 26,705 tweets) makes it less practical for this use case. Therefore, for projects requiring a balance of speed and accuracy, `DistilBERT` is recommended.


### Usage

To use this project, you need to have Python installed on your system. Additionally, you need to install the required libraries, which include TextBlob, NLTK (for VADER), and transformers (for roBERTa and distilBERT). You also need access to the Twitter API and OAuth v2.0 credentials. You can install the required libraries using pip:

```python
pip install textblob nltk transformers
```

To access the Twitter API, you need to apply for a developer account and create an application. Once your application is approved, you will receive the OAuth v2.0 credentials.

### Contributing

Contributions to this project are welcome. If you have a proposal or modification, please follow these steps:

1. Fork the repository.
2. Create a new branch in your forked repository.
3. Make your changes in the new branch.
4. Submit a pull request from the new branch in your forked repository to the main branch in the original repository.

Before submitting your pull request, please ensure your changes do not break any existing functionality and that they adhere to the existing coding style.

### License

This project is licensed under the terms of the MIT License. This means you are free to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software, provided that you include the following copyright notice and permission notice in all copies or substantial portions of the software:

```text
Copyright (c) [2024] [DivyaSharma]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```
