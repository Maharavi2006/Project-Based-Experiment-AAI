<H3>ENTER YOUR NAME: MAHALAKSHMI R</H3>
<H3>ENTER YOUR REGISTER NO: 212223230117 </H3>

<H1 Align="center">Project Based Experiment<H1>
<H3>Objective:<H3>
The objective of this project is to analyze Facebook post comments or feedback using sentiment analysis and filter only those entries that have positive sentiment. This helps in understanding user engagement and extracting constructive insights from social media data.
<H3>Program:</H3>
  
```
import pandas as pd
from textblob import TextBlob
import matplotlib.pyplot as plt
```
  
### Step 1: Load Facebook data (CSV format)

### Step 2: Sentiment analysis function

### Step 3: Apply sentiment function to each comment

### Step 4: Filter only Positive feedback

### Step 5: Save to a new CSV

### Step 6: Visualization - Bar chart of sentiment distribution

### Step 7: Display some positive comments
## Program:
```py
import nltk
from nltk.sentiment import SentimentIntensityAnalyzer

nltk.download('vader_lexicon')

sia = SentimentIntensityAnalyzer()

n = int(input("Enter number of feedbacks: "))

neutral_feedback = []

for i in range(n):
    text = input(f"Enter feedback {i+1}: ")

    score = sia.polarity_scores(text)["compound"]

    if score >= 0.05:
        sentiment = "Positive"
    elif score <= -0.05:
        sentiment = "Negative"
    else:
        sentiment = "Neutral"

    print(f"Sentiment: {sentiment}")
    print(f"Score: {score}\n")

    if sentiment == "Neutral":
        neutral_feedback.append(text)

print("\n========== NEUTRAL FEEDBACK ==========")

if len(neutral_feedback) == 0:
    print("No neutral feedback found.")
else:
    for feedback in neutral_feedback:
        print("-", feedback)
```
<H3>Output:</H3>
<img width="514" height="459" alt="image" src="https://github.com/user-attachments/assets/da353a2f-0efc-4be5-951d-d44fec462fef" />


<H3>Inference:</H3>
In this project, I learned how to use Python to perform basic sentiment analysis on text data. I was able to classify comments as positive, negative, or neutral and filter out the positive feedback. This helped me get hands-on practice with Python libraries like pandas and TextBlob and understand how sentiment analysis works on social media data.
