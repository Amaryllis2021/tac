# Projet RAG CaMille : analyse du commerce belge dans les années 1970


#CONTEXTE ACADÉMIQUE

Ce projet a été réalisé dans un cadre académique pour illustrer :les systèmes RAG modernes, ingénierie de prompts et la recherche d’information dense.

Ce projet vise à analyser le commerce belge dans les années 1970 en utilisant des techniques de Récupération Augmentée par Génération (RAG) et le corpus Camille. L'objectif est de comprendre

les tendances commerciales, les flux d'importation et d'exportation, ainsi que les facteurs économiques influençant le commerce durant cette période.

Ce projet implémente un système Retrieval‑Augmented Generation (RAG) appliqué à un corpus historique d’environ 689 fichiers texte (.txt) portant sur le commerce et l’économie en Belgique dans les années 1970.

L’objectif est de permettre à un modèle de langage (LLM) de répondre à des questions complexes en s’appuyant explicitement sur des documents sources, plutôt que sur sa seule connaissance interne.

Le travail s’inspire directement de l’article fondateur : Lewis et al. (2020) – Retrieval‑Augmented Generation for Knowledge‑Intensive NLP Tasks

https://arxiv.org/abs/2005.11401 .  J´ai implementé cette architecture au corpus pCaMille en utilisant une pile modulaire d'outils modernes (FAISS, LangChain, Ollama) pour créer un pipeline de 

recherche et de génération similaire dans son esprit, bien que modulaire dans son implémentation.

#Objetifs du projet

Explorer les principes théoriques du RAG

Implémenter un pipeline RAG fonctionnel de bout en bout

Indexer un corpus documentaire local volumineux

Réduire les hallucinations du LLM grâce à la récupération de contexte

Générer des réponses factuelles, contextualisées et traçables


#Structure du projet
Le projet est structuré en plusieurs étapes clés :
1. Préparation des données : Nettoyage et structuration du corpus Camille.
2. Indexation : Utilisation de techniques d’indexation pour organiser les documents.
3. Récupération : Mise en place d’un système de récupération d’informations pertinent.
4. Génération : Intégration d’un LLM pour générer des réponses basées sur les documents récupérés.
5. Évaluation : Analyse de la performance du système RAG en termes de précision et de fiabilité des réponses dans um rapport au corpus historique.

#Méthodologie technique
1. Chargement du corpus obtenu via data_preparation

Lecture automatique de tous les fichiers .txt (689)

Ajout de métadonnées (source, année, fichier)

2. Découpage sémantique

Utilisation de RecursiveCharacterTextSplitter

Chunks de taille contrôlée avec chevauchement

3. Vectorisation

Embeddings générés via OllamaEmbeddings

Modèle utilisé : nomic-embed-text

4. Indexation FAISS

Index dense pour recherche rapide

Similarité cosinus

Scalabilité sur plusieurs centaines de documents

5. Génération de réponse

Sélection des top‑k chunks les plus pertinents

Construction d’un prompt structuré

Génération avec ChatOllama (Llama 3)



#Technologies utilisées
Python 3.11

Ollama (LLM + embeddings) : Moteur d'exécution local pour le LLM (modèle génératif) et la création d'embeddings.

FAISS (recherche vectorielle, Facebook AI Similarity Search) : Bibliothèque pour l'indexation vectorielle et la recherche efficace dans de grands ensembles de données.

LangChain (modulaire) : Framework pour orchestrer le pipeline RAG (chargeurs de documents, splitters, chaînes de traitement).

NumPy / Pandas


#Installation & Configuration
Prérequis
Python 3.10 ou supérieur

Ollama installé et le modèle llama3 (ou autre) téléchargé.

Git


#Instructions pour l'exécution
1. Cloner le dépôt GitHub du projet.
2. Installer les dépendances requises via pip.
3. Préparer le corpus Camille en suivant les instructions dans le dossier data_preparation.
4. Exécuter les scripts d'indexation et de récupération.
5. Lancer le module de génération pour obtenir des réponses aux questions posées.   
6. Consulter les résultats et le rapport final.


Licence
Ce projet est distribué sous licence MIT. Voir le fichier LICENSE pour plus de détails.

Remerciements et références
Lewis, P., et al. (2020). Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks. arXiv:2005.11401. (Inspiration fondamentale)

Les équipes derrière Ollama, LangChain, FAISS et la communauté Hugging Face pour leurs outils extraordinaires.

La communauté open-source et du Kaggle pour le partage des connaissances qui rend ce genre de projet possible.

#Auteur
Projet réalisé par : Amarílis Pêgo, 2025