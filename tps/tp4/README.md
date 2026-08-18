# TP4: Travail final
# Traitement automatique de corpus
# Auteur: Amarilis PEGO

import streamlit as st
import pandas as pd
import os
import nltk
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer
import multiprocessing

# Téléchargement des ressources NLTK 
nltk.download('stopwords')
nltk.download('wordnet')

# Fonction de prétraitement (à personnaliser)
def preprocess(text):
    # Tokenisation, mise en minuscules
    words = nltk.word_tokenize(text.lower())
    # Suppression des stop words
    stop_words = set(stopwords.words('french'))  # Adapter à la langue
    words = [word for word in words if word not in stop_words]
    # Lemmatisation
    lemmatizer = WordNetLemmatizer()
    words = [lemmatizer.lemmatize(word) for word in words]
    return " ".join(words)

# Fonction pour lire et prétraiter un fichier
def process_file(file_path):
    df = pd.read_excel(file_path)
    df['text'] = df['text'].apply(preprocess)  # Colonne 'text' à adapter
    return df

# Répertoire contenant les fichiers
data_dir = "path/to/your/data"

# Liste des fichiers
files = [os.path.join(data_dir, f) for f in os.listdir(data_dir) if f.endswith('.xlsx')]

# Création d'une pool de processus pour le parallélisme
with multiprocessing.Pool() as pool:
    dfs = pool.map(process_file, files)

# Concaténation des DataFrames
df_final = pd.concat(dfs, ignore_index=True)

# Enregistrement du corpus
df_final.to_csv("corpus_femmes.csv", index=False)

# Création du corpus pour l'analyse NLP
corpus = df_final['text'].tolist()