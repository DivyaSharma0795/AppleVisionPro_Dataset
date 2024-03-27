# Sentiment Analysis on Apple Vision Pro Tweets

This project revolves around gathering tweets concerning the Apple Vision Pro from January 1, 2024, to March 16, 2024, and conducting sentiment analysis on them. The product was unveiled on January 8, 2024, and was made available on February 2, 2024.

### Data Collection
Twitter's API with OAuth v2.0 was utilized to collect the data. The tweets were filtered to exclusively include those referencing the Apple Vision Pro.

### Sentiment Analysis
The sentiment analysis was executed via four distinct methodologies:

-  `TextBlob`: A Python library tailored for processing textual data, offering a straightforward API for various natural language processing (NLP) tasks such as sentiment analysis.
-  `VADER (Valence Aware Dictionary and sEntiment Reasoner)`: A lexicon and rule-based sentiment analysis tool finely attuned to sentiments expressed in social media.
-  `roBERTa`: A transformer-based model developed by Facebook's AI team, a variant of BERT finely optimized for NLP tasks.
-  `distilBERT`: A lighter, faster, and more economical version of BERT crafted by Hugging Face, also a transformer-based model widely employed for NLP tasks, including sentiment analysis.

### Results
The sentiment analysis outcomes are presented in a comparative format, facilitating a comprehensive grasp of the public sentiment towards the Apple Vision Pro within the specified timeframe.

### Usage
To utilize this project, ensure Python is installed on your system, alongside the required libraries (TextBlob, NLTK for VADER, transformers for roBERTa and distilBERT). Additionally, access to the Twitter API and possession of OAuth v2.0 credentials are essential.

### Contributing
Contributions are encouraged. Please initiate an issue to discuss your proposal or submit a pull request containing your modifications.

### License
This project is licensed under the terms of the GNU Public License.
