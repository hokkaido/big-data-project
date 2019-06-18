# Generating fake reviews 

This is part of a project that I've done for a Machine Intelligence course at the Zurich University of Applied Sciences. Since its focus was on big data,
Apache Spark is involved at some stages. 

## What does it do

The idea is to generate fake reviews based on [Yelp's review dataset](https://www.kaggle.com/yelp-dataset/yelp-dataset) and then try to detect them with more traditional ML methods.

1. Data wrangling with PySpark, tokenisation with CoreNLP from Stanford
2. Training a Seq2Seq model with a fork of [OpenNMT-py](https://github.com/hokkaido/OpenNMT-py/tree/translate-improvements), this part is heavily inspired by [Stay On-Topic: Generating Context-specific Fake Restaurant Reviews](https://arxiv.org/abs/1805.02400) by Juuti et al. 
3. Training various classifiers with Spark ML that try to distinguish between fake and and real reviews.


## Some sample outputs

The Seq2Seq model was able to generate rather convincing looking fake reviews:

    SENT 1: ['4.0', 'las', 'vegas', 'restaurants', ',', 'vietnamese']
    PRED 1: i love this place ! the food is always fresh and delicious . it 's a little pricey , but worth every penny .
    PRED SCORE: -33.2517

    SENT 2: ['1.0', 'calgary', 'asian', 'fusion', ',', 'chicken', 'wings', ',', 'food', ',', 'cafes', ',', 'chinese', ',', 'desserts', ',', 'juice', 'bars', '&', 'smoothies', ',', 'restaurants']
    PRED 2: this is the worst bubble tea place i 've ever been to . it 's so expensive and they do n't have a lot of options .
    PRED SCORE: -36.3755

    SENT 3: ['3.0', 'scottsdale', 'japanese', ',', 'nightlife', ',', 'restaurants', ',', 'sushi', 'bars']
    PRED 3: this is a good place to go if you 're in the mood for japanese food . it 's not bad , but nothing special .
    PRED SCORE: -36.7155