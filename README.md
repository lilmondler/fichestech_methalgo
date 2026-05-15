# # Cartographie des sous-cultures numériques  
Cartographie des sous-cultures numériques : Analyse comparative des communautés incels et femcels sur Reddit
## Fiche technique

### Réalisé par  
**Snezhana Galimova**  
Master 1 Sociologie — Chargé(e) d’études sociologiques  
Sorbonne Université  
Année universitaire 2025–2026

---

# Présentation du projet

Ce projet propose une analyse comparative de deux sous-cultures numériques présentes sur Reddit : les communautés **incels** et **femcels**.

L’objectif est d’étudier si ces espaces peuvent être considérés comme des communautés discursives distinctes, possédant leurs propres caractéristiques :

- linguistiques ;
- émotionnelles ;
- structurelles.

L’analyse mobilise plusieurs méthodes de traitement automatique du langage naturel (NLP) afin de comparer les contenus publiés dans les deux communautés.

---

# Hypothèses

## H1 — Convergence linguistique

Les communautés incels et femcels partagent-elles un vocabulaire suffisamment similaire pour empêcher leur distinction automatique ?

Hypothèse :
les deux groupes possèdent des registres lexicaux distincts permettant une classification automatique des publications.

---

## H2 — Asymétrie émotionnelle

Les deux communautés expriment-elles des profils émotionnels différents ?

Hypothèse :
le discours incel présente une polarisation émotionnelle plus forte et davantage de négativité.

---

## H3 — Chambre d’écho

La structure des interactions révèle-t-elle un effet de chambre d’écho ?

Hypothèse :
une faible minorité d’auteurs très actifs produit une grande partie du contenu dans les communautés incels.

---

# Données

Les données utilisées proviennent des subreddits :

- `r/Incels`
- `r/Truefemcels`

Les corpus ont été exportés au format CSV puis harmonisés avant l’analyse.

---

# Méthodologie

L’analyse repose sur un pipeline en plusieurs étapes.

## 1. Prétraitement des données

Les textes ont été normalisés afin de rendre les corpus comparables.

Le prétraitement comprend :

- conversion en minuscules ;
- suppression des URLs ;
- suppression des mentions Reddit ;
- suppression de la ponctuation ;
- suppression des stopwords ;
- suppression du bruit de plateforme ;
- lemmatisation via WordNetLemmatizer.

---

## 2. Analyse fréquentielle

Une analyse des mots les plus fréquents a été réalisée afin d’identifier les thèmes dominants de chaque communauté.

---

## 3. TF-IDF + Régression Logistique

Le modèle TF-IDF permet de pondérer les mots selon leur importance relative dans chaque corpus.

Une régression logistique est ensuite utilisée afin de prédire automatiquement la communauté d’origine des publications.

---

## 4. Analyse de sentiment (VADER)

L’outil VADER permet de mesurer automatiquement :

- la positivité ;
- la négativité ;
- la neutralité ;
- le score émotionnel global (*compound*).

---

## 5. Analyse structurelle

Une analyse de concentration des auteurs a été réalisée afin d’évaluer la présence d’effets de chambre d’écho.

Deux indicateurs ont été utilisés :

- concentration du contenu par centiles d’auteurs ;
- Type-Token Ratio (TTR).

---

# Principaux résultats

## H1 — Distinction linguistique forte

Le classifieur atteint une accuracy proche de 100 %, ce qui indique que les deux communautés possèdent des registres lexicaux fortement distincts.

Les mots discriminants révèlent également des différences importantes dans les thèmes dominants et les styles discursifs.

---

## H2 — Polarisation émotionnelle chez les incels

Les distributions émotionnelles des incels sont plus étalées.

On observe :

- davantage de messages très négatifs ;
- davantage de messages très positifs ;
- une intensité émotionnelle plus forte.

Les femcels présentent des distributions plus resserrées et émotionnellement plus homogènes.

---

## H3 — Forte concentration du contenu chez les incels

Les résultats montrent une forte centralisation du discours incel.

- le top 1 % des auteurs produit environ 57 % du contenu ;
- le top 5 % produit plus de 80 % du corpus ;
- le top 10 % produit près de 88 % des publications.

Chez les femcels, la distribution du contenu est beaucoup plus diffuse.

Cette concentration suggère un fonctionnement proche d’une chambre d’écho.

---

# Reproductibilité

Le notebook peut être exécuté dans l’ordre indiqué dans le dossier `/notebooks`.

---

# Limites

Cette étude présente plusieurs limites :

- déséquilibre entre les corpus ;
- taille réduite du corpus femcel ;
- représentativité limitée des données Reddit ;
- simplification des émotions par les outils automatiques de NLP.

---

# Poster scientifique

Le poster présenté dans le cadre du cours  `/poster`.

---

# Technologies utilisées

- Python
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- nltk
- vaderSentiment
