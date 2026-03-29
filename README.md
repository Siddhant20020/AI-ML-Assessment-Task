Overview

This project is a content-based movie recommendation system built using NLP techniques.
It recommends movies based on their plot descriptions using TF-IDF vectorization and cosine similarity.

The system allows users to get recommendations by:

i.Movie title 

ii.Custom description

iii.Optional genre filtering


Objective

The goal of this project is to build a recommendation system without using pre-trained embeddings, relying only on:

i.Bag-of-Words / TF-IDF

ii.Traditional NLP preprocessing techniques


Dataset

Source: Hugging Face – jquigl/imdb-genres

Fields used:

title – Movie name

description – Plot summary

genre – Movie genre

ratings – Movie rating

Train split is used for building the model and validation split for testing.


Approach

1. Data Preprocessing

   I cleaned the text data using:

i.Lowercasing all text

ii.Removing punctuation

iii.Removing stopwords (using NLTK)

This helps reduce noise and improves vectorization quality.


2. Vectorization

I used TF-IDF (Term Frequency – Inverse Document Frequency) to convert movie descriptions into numerical vectors.

Why TF-IDF?

i.It gives importance to meaningful words

ii.Reduces the effect of very common words


3. Similarity Computation

Instead of computing a full similarity matrix (which is memory expensive), I compute cosine similarity on-the-fly between:

i.Input movie/description

ii.All movies in the dataset

This makes the system more efficient and scalable.


4. Recommendation Logic
i.If a title is given → find similar movies based on its description

ii.If a description is given → match with similar movie plots

iii.If genre is provided → filter recommendations


The system returns Top 5 most similar movies.


Example Usage

recommend_movies(title="Inception")

recommend_movies(description="space adventure aliens future war")

recommend_movies(title="Inception", genre="Action")


Evaluation

I used Precision@K to evaluate recommendation quality.

It measures how many recommended movies match the genre of the input movie.
Example:
precision_at_k("The Dark Knight", k=5)


Limitations
The system does not understand semantic meaning (e.g., synonyms like "car" vs "vehicle")

No personalization (same results for every user)

Cold start problem for new or missing movies


 Future Improvements

If I were to extend this project, I would:

Use word embeddings (Word2Vec, BERT) for better semantic understanding

Build a hybrid system combining content-based + collaborative filtering

Add ranking using ratings and popularity


Tech Stack

Python

Pandas

Scikit-learn

NLTK


Setup Instructions

i. Clone the repository:

git clone https://github.com/Siddhant20020/AI-ML-Assessment-Task.git

ii.Install dependencies


iii.Run the notebook


Conclusion

This project demonstrates how a basic NLP pipeline can be used to build a functional recommendation system without relying on heavy models or pre-trained embeddings.

It focuses on simplicity, efficiency, and clarity of implementation.







