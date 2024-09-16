# Auditing a Speech-to-Text API

_By Ariana Rosario (ar943)_

## Introduction

### Google's Speech-to-Text API

The Speech-to-Text API is one of GCP's Free Tier products (up to 60 mins/mo) that generates transcribes text from audio. Besides the transcription, the API response also includes metadata such as the confidence score which I included into the results dataframe in case it could come in handy during the analysis. Here's more information about the API: https://cloud.google.com/speech-to-text

### The Data

I initially wanted to test the API using **Facebook's voxpopuli dataset** since it included rich demographic information about the speakers such as accents and native language. I wanted to test the _API's performance for non-native English speakers_, (especially for native Spanish speakers since it was relatable). However, after dealing with multiple issues loading the data, I ultimately decided to use a different dataset. Here's more information about voxpopuli: https://huggingface.co/datasets/facebook/voxpopuli

#### Mozilla's Common Voice Dataset

In the end, I went with **Mozilla's Common Voice dataset** which is widely used for speech recognition tasks. The dataset consists of audio clips and their corresponding metadata including the "ground truth" transcription as well as information about the speaker (such as Age and Gender). While I wouldn't be able to test the API's performance for non-native English speakers with this dataset, I thought could potentially observe _differences across gender groups._ Here's more information about the dataset: https://commonvoice.mozilla.org/en/datasets

### Hypothesis

Given that the API was developed by Google, and it's supposedly used in their own products, **I expect it to perform decently well.** There's also the fact that the dataset is pretty popular (although I downloaded the Delta Segment 16.1 subset which only includes the most recent entries).
However, I'm curious to see whether there are any **differences in how the API performs for speakers of different genders.**

## Discussion

As seen in the plots above, **the API performed differently across gender groups.**

For once, the median Word Error Rate (WER) for male speakers was fairly decent at ~30% while one for female speakers was significantly higher at ~45%. Another thing I noticed was that the confidence scores provided by the API were slightly higher for men (almost 90% median confidence score) vs. women (~83% median confidence score).

Additionally, in both cases, the confidence scores were negatively correlated with the WER _(which makes sense)_. However, the correlation was stronger for male speakers and female speakers has more outliers.

In the end, I didn't expect to see such a big difference in performance. I figured that, at this point, these models would be incredibly good at transcribing speech.

### Possible Explanations

My initial guess is that the difference in performance across gender could be due to the model being trained on a dataset that's not representative of the general population. In other words, **maybe there wasn't enough data from women in the training dataset.**

Another thing that comes to mind is that women's tone and pitch can be considerably different than men's and if there wasn't enough data from female speakers, the model might not have been able to learn their speech patterns as well.

### Limitations

While there are considerable differences in the API's performance for male and female speakers, it's important to note that _the dataset I used is very small._

I only transcribed 20 random audio clips for each gender group, so it's very likely that **there weren't enough data points for the results to be significant.**

Also, I only used WER and confidence scores to evaluate the API. There are probably many other metrics to consider in order to get a more in-depth analysis.

## References

#### Researching Datasets

- https://paperswithcode.com/datasets?mod=audio&lang=english
- https://web.stanford.edu/class/cs224s/datasets/
- https://commonvoice.mozilla.org/en/datasets
- https://huggingface.co/datasets/common_voice

#### Setting up GCP

- https://cloud.google.com/speech-to-text
- https://youtu.be/xKvffLRSyPk?si=LXrXfJyLCvzH1J62
- https://youtu.be/izdDHVLc_Z0?si=qcRQL4QHZJsFX4LB

#### Speech-to-text API Tutorial

- https://youtu.be/jBbLon5esbE?si=pNd4Bsc6aCUBftUO

#### Word Error Rate

- https://pypi.org/project/jiwer/
- https://medium.com/@johnidouglasmarangon/how-to-calculate-the-word-error-rate-in-python-ce0751a46052

#### Plotting

- https://seaborn.pydata.org/
- https://python-charts.com/correlation/scatter-plot-regression-line-seaborn/
