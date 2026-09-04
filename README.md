<H3>ENTER YOUR NAME</H3>
MAHALAKSHMI R

<H3>ENTER YOUR REGISTER NO.</H3>
212223230117

<H3>DATE:</H3>
04-09-2026

<H1 Align="center">Project Based Experiment</H1>

<H3>Objective:</H3>
To analyze the sentiments of Facebook user posts and classify them into Positive, Negative, or Neutral categories using NLTK’s VADER sentiment analysis approach.

<H3>Program:</H3>

```python
import pandas as pd
from nltk.sentiment.vader import SentimentIntensityAnalyzer
import nltk
import re

nltk.downloader.download('vader_lexicon')

# Load dataset
df = pd.read_csv('fb_sentiment.csv')

# Simple positive and negative keyword sets (you can expand these)
positive_words = ['good', 'great', 'happy', 'love', 'excellent', 'best', 'wonderful', 'positive', 'awesome', 'fantastic']
negative_words = ['bad', 'terrible', 'sad', 'hate', 'worst', 'awful', 'horrible', 'negative', 'poor', 'angry']

# Basic text cleaning and sentiment classification
def simple_sentiment(text):
    text = str(text).lower()
    text = re.sub(r'[^a-z\s]', '', text)
    pos_count = sum(1 for word in positive_words if word in text)
    neg_count = sum(1 for word in negative_words if word in text)
    if pos_count > neg_count:
        return 'Positive'
    elif neg_count > pos_count:
        return 'Negative'
    else:
        return 'Neutral'

# Apply sentiment function
df['Predicted_Sentiment'] = df['FBPost'].apply(simple_sentiment)

# Display summary
print(df['Predicted_Sentiment'].value_counts())

# Save results to Excel
df.to_excel('fb_sentiment_results.xlsx', index=False)
print("✅ Sentiment results saved to 'fb_sentiment_results.xlsx'")

import pandas as pd
import matplotlib.pyplot as plt
from nltk.sentiment.vader import SentimentIntensityAnalyzer
import nltk

# Download the VADER lexicon
nltk.download('vader_lexicon')

# Load your dataset
df = pd.read_csv('fb_sentiment.csv')

# Initialize Sentiment Analyzer
sia = SentimentIntensityAnalyzer()

# Predict sentiment
def vader_sentiment(text):
    score = sia.polarity_scores(str(text))['compound']
    if score >= 0.05:
        return 'Positive'
    elif score <= -0.05:
        return 'Negative'
    else:
        return 'Neutral'

df['Predicted_Sentiment'] = df['FBPost'].apply(vader_sentiment)


# Show distribution
print(df['Predicted_Sentiment'].value_counts())

# Visualization — Bar Chart
plt.figure(figsize=(6,4))
df['Predicted_Sentiment'].value_counts().plot(kind='bar', color=['#10b981','#ef4444','#3b82f6'])
plt.title('Sentiment Distribution (VADER Analysis)')
plt.xlabel('Sentiment Category')
plt.ylabel('Number of Posts')
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()

# Visualization — Pie Chart
plt.figure(figsize=(5,5))
df['Predicted_Sentiment'].value_counts().plot(kind='pie', autopct='%1.1f%%', startangle=90, colors=['#10b981','#ef4444','#3b82f6'])
plt.title('Sentiment Percentage (VADER Analysis)')
plt.ylabel('')
plt.show()

# Save to Excel
df.to_excel('fb_sentiment_vader_results.xlsx', index=False)
print("✅ Sentiment results saved to 'fb_sentiment_vader_results.xlsx'")

# Show sample results
print("Sample Positive Feedback:\n")
positive_samples = df[df['Predicted_Sentiment'] == 'Positive'][['FBPost', 'Predicted_Sentiment']].head(5)
print(positive_samples.to_string(index=False))

print("\nSample Negative Feedback:\n")
negative_samples = df[df['Predicted_Sentiment'] == 'Negative'][['FBPost', 'Predicted_Sentiment']].head(5)
print(negative_samples.to_string(index=False))

print("\nSample Neutral Feedback:\n")
neutral_samples = df[df['Predicted_Sentiment'] == 'Neutral'][['FBPost', 'Predicted_Sentiment']].head(5)
print(neutral_samples.to_string(index=False))
```

<H3>Output:</H3>

![alt text](image.png)

![alt text](image-1.png)

![alt text](image-2.png)

![alt text](image-3.png)

<pre>
Sample Positive Feedback:

                                                                                                                                                                                                                                                                                                                                                                                                         FBPost Predicted_Sentiment
@Maria:  Do you mean the Nook?  Be careful, books you buy for the Kindle are for that piece of electronics, and vice versa.  I love my Kindle, there are people that swear by the Nook.  They like the color screen.Me?  I want an ereader that is a reader-- so I dont need color.  The kindle battery lasts longer, and the unit isnt as heavy, which can make a difference after reading for a few hours. :)            Positive
                                                                                                                                                                                                                                                                                                                                                                                 kindle is awesome! mines great            Positive
                                                                                                                                                                                                                                                                                                                                                                                                I love mine!!!!            Positive
                                                                                                                                                                                                                                                                                                                                                                                       My daugjhter loves hers!            Positive
                                                                                                                                                                                                                                                                           Got a Kindle for Xmas and I love it.   Never was much of a book reader, but this has been fun.  I am on my 5th book since Christmas!            Positive

Sample Negative Feedback:

                                                                                                                                                                                                                                                     FBPost Predicted_Sentiment
          Drug Runners and  a U.S. Senator have something to do with the Murder http://www.amazon.com/Circumstantial-Evidence-Getting-Florida-Bozarth-ebook/dp/B004FPZ452/ref=pd_rhf_p_t_1 The State Attorney Knows... NOW So Will You. GET Ypur Copy TODAY            Negative
Heres a single, to add, to Kindle. Just read this 19th century story: "The Ghost of Round Island". Its about a man (French/American Indian) and his dog sled transporting a woman across the ice, from Mackinac Island to Cheboygan - and the ghost that...            Negative
                                                                                                                                                                                                            Ghost of Round Island is supposedly nonfiction.            Negative
                                         Meh. I think Singles are a bad idea. Big name authors already dominate the market by a huge factor. Now you are letting them compete on price point with indie authors (albeit giving less content for the money).            Negative
                                                                                 I am not sure if i just got my update but now i dont have location numbers unless i press the menu button.  But i also dont have page numbers! Am i doing something wrong?            Negative

Sample Neutral Feedback:

                                                                                                                                            FBPost Predicted_Sentiment
If you tire of Non-Fiction.. Check out http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=danielle+lee+zwissler+&x=0&y=0             Neutral
                                                            Why is Barnes and Nobles version of the Kindle so much more expensive than the Kindle?             Neutral
                                                         I dont have the patience for kindle singles. If Im gonna read, I need at least 200 pages.             Neutral
                                                                                                                                 What is a single?             Neutral
                                                           anyone know how to legthen the time before the kindle go into screen saver mood????????             Neutral

</pre>

<H3>Inference:</H3>
Through this project, I learned how to perform sentiment analysis using natural language processing techniques.  
I understood how **NLTK’s VADER (Valence Aware Dictionary and sEntiment Reasoner)** can effectively classify short social media texts into positive, negative, and neutral sentiments.  
Additionally, I learned data preprocessing using **Pandas**, model-based sentiment scoring, and how to visualize the sentiment distribution using **matplotlib**.  
This project helped me understand real-world applications of AI and NLP in analyzing public opinion from social media data.
