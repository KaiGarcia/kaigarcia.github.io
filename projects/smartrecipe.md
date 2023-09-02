---
layout: project
type: project
image: img/scikit-learn-logo.png
title: "Smart Recipe Recommender"
date: 2023
published: true
labels:
  - Python
  - Machine Learning
  - TF-IDF
  - Culinary
summary: "A Smart Recipe Recommender system that leverages artificial intelligence and machine learning."
---

This is a sample of a Smart Recipe Recommender system that leverages artificial intelligence and machine learning techniques to provide personalized recipe suggestions to users. Users can create profiles specifying their dietary preferences, ingredient availability, and cooking skill levels. The system then analyzes this information along with a database of recipes, employing TF-IDF vectorization and cosine similarity to recommend recipes that align with the user's preferences and constraints. It's a simplified console-based application that demonstrates the core recommendation logic and can serve as a starting point for a more extensive and user-friendly recipe recommendation platform, offering culinary inspiration tailored to individual tastes and cooking abilities.

Here is some example code to illustrate sample dataset use:

```python
import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import linear_kernel

# Sample recipe data (You can replace this with a larger dataset)
recipes = pd.DataFrame({
    'RecipeID': [1, 2, 3, 4],
    'Title': ['Spaghetti Carbonara', 'Vegetable Stir-Fry', 'Chicken Alfredo', 'Chocolate Cake'],
    'Ingredients': ['spaghetti, eggs, bacon, Parmesan cheese', 'broccoli, carrots, tofu, soy sauce', 
                    'chicken breast, heavy cream, Parmesan cheese', 'flour, sugar, cocoa powder, eggs'],
})

# Sample user preferences
user_preferences = 'chicken, cream, Parmesan cheese'

# Calculate TF-IDF vectors for recipe ingredients
tfidf_vectorizer = TfidfVectorizer()
tfidf_matrix = tfidf_vectorizer.fit_transform(recipes['Ingredients'])

# Calculate cosine similarity between user preferences and recipes
cosine_sim = linear_kernel(tfidf_matrix, tfidf_vectorizer.transform([user_preferences]))

# Get top recipe recommendations
recipe_indices = cosine_sim[0].argsort()[::-1]
top_recipe_indices = recipe_indices[1:4]  # Exclude the first item (itself)
recommended_recipes = recipes.iloc[top_recipe_indices]

# Display recommended recipes
print("Recommended Recipes:")
for idx, row in recommended_recipes.iterrows():
    print(f"{row['Title']}: {row['Ingredients']}")

```
 
[TfidfVectorizer Documentation]([url](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html)): https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html

[linear_kernel Documentation]([url](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.linear_kernel.html)): https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.linear_kernel.html
