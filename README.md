Cartographie des sous-cultures numériques

Analyse comparative des communautés incels et femcels sur Reddit
Réalisé par

Snezhana Galimova
Master 1 Sociologie — Chargé(e) d’études sociologiques
Sorbonne Université
Année universitaire 2025–2026

Présentation du projet

Ce projet propose une analyse comparative de deux sous-cultures numériques présentes sur Reddit : les communautés incels et femcels.

Ces deux espaces sont souvent présentés comme des « miroirs genrés » l’un de l’autre. L’objectif de ce travail est donc de vérifier si leurs discours fonctionnent réellement de manière similaire, ou s’ils possèdent au contraire des caractéristiques propres sur le plan :

linguistique ;
émotionnel ;
structurel.

L’analyse mobilise plusieurs outils de traitement automatique du langage naturel (NLP) afin d’explorer les différences entre les deux communautés.

Hypothèses
H1 — Convergence linguistique

Malgré des positions genrées opposées, les deux communautés partagent-elles un vocabulaire et des thématiques suffisamment similaires pour qu’un classifieur automatique ait du mal à les distinguer ?

H2 — Asymétrie émotionnelle

Les émotions exprimées prennent-elles des formes différentes dans les deux communautés ?

Hypothèse :
le discours incel présenterait une polarisation émotionnelle plus forte et des formes de négativité plus intenses.

H3 — Chambre d’écho

Une forte concentration du contenu autour d’un petit noyau d’auteurs, combinée à un vocabulaire répétitif, peut-elle révéler un fonctionnement en chambre d’écho ?

Données

Les données utilisées proviennent des subreddits :

r/Incels
r/Truefemcels

Les corpus ont été exportés au format CSV puis harmonisés avant l’analyse.

Après traitement :

corpus incels : plus de 929 000 publications ;
corpus femcels : 258 publications.

Ce déséquilibre constitue une limite importante de l’étude et impose de rester prudent dans l’interprétation des résultats concernant les femcels.

Méthodologie

L’analyse repose sur plusieurs étapes complémentaires.

1. Prétraitement NLP

Les textes sont nettoyés et normalisés afin de rendre les corpus comparables.

Le pipeline comprend :

conversion en minuscules ;
suppression des URLs ;
suppression des mentions Reddit ;
suppression de la ponctuation et des chiffres ;
suppression des stopwords anglais ;
suppression du bruit de plateforme Reddit ;
tokenisation ;
lemmatisation avec WordNetLemmatizer.
2. Classification automatique (H1)

Un pipeline TfidfVectorizer + LogisticRegression est entraîné afin de prédire automatiquement la communauté d’origine de chaque publication.

L’objectif est de tester si les deux communautés sont suffisamment proches lexicalement pour tromper le modèle.

L’analyse des coefficients permet également d’identifier les mots les plus discriminants de chaque communauté.

3. Paysage textuel

Deux représentations numériques du texte sont utilisées :

CountVectorizer (Bag-of-Words) ;
TfidfVectorizer.

Le Bag-of-Words mesure la fréquence brute des mots, tandis que le TF-IDF met davantage en valeur les termes caractéristiques d’une communauté.

Une analyse du chevauchement lexical est également réalisée afin d’évaluer la part du vocabulaire partagé entre les deux groupes.

4. Analyse de sentiment (H2)

L’outil VADER est utilisé afin de mesurer automatiquement :

le score positif (pos) ;
le score négatif (neg) ;
le score neutre (neu) ;
le score global (compound).

L’analyse compare :

les distributions émotionnelles ;
l’intensité des émotions ;
le lien entre négativité et participation.
5. Analyse structurelle (H3)

Une analyse de concentration des auteurs permet d’évaluer la présence d’effets de chambre d’écho.

Deux indicateurs sont mobilisés :

Concentration du contenu

Part du contenu produite par les auteurs les plus actifs :

top 1 % ;
top 5 % ;
top 10 %.
Richesse lexicale (TTR)

Le Type-Token Ratio (TTR) mesure la diversité du vocabulaire utilisé par différents groupes d’auteurs.

Une baisse du TTR chez les auteurs hyperactifs peut signaler un discours plus répétitif et homogène.

Principaux résultats
H1 — Distinction linguistique forte

Le classifieur atteint une accuracy proche de 100 %.

Cependant, ce résultat doit être nuancé : le fort déséquilibre entre les corpus pousse le modèle à prédire majoritairement la classe incel.

Malgré cela, les mots discriminants montrent des différences importantes entre les univers discursifs des deux communautés.

H2 — Intensité émotionnelle plus forte chez les incels

Les distributions émotionnelles des incels apparaissent plus étalées :

davantage de messages très négatifs ;
davantage de messages très positifs ;
polarisation émotionnelle plus forte.

Les profils émotionnels femcels semblent plus homogènes, mais le faible volume de données limite les conclusions possibles.

H3 — Forte concentration du contenu chez les incels

Les résultats montrent une forte centralisation du discours incel :

le top 1 % des auteurs produit environ 57 % du contenu ;
le top 5 % produit plus de 80 % du corpus ;
le top 10 % produit près de 88 % des publications.

Chez les incels, les auteurs les plus actifs utilisent également un vocabulaire plus répétitif (TTR faible), ce qui suggère un fonctionnement proche d’une chambre d’écho.

Cartographie temporelle

Une analyse temporelle des pics d’activité a également été explorée.

Cependant, cette partie n’a pas été retenue dans le poster final en raison :

du faible volume de données femcels ;
du risque de surinterprétation des pics d’activité ;
de l’impossibilité d’attribuer avec certitude ces variations à des événements externes précis.
Limites

Cette étude présente plusieurs limites :

déséquilibre important entre les corpus ;
faible taille du corpus femcel ;
représentativité limitée des données Reddit ;
simplification des émotions par les outils automatiques de NLP ;
difficulté d’interpréter certains pics temporels sans contexte externe.
Structure du projet
/notebooks — notebook principal d’analyse
/poster — poster scientifique du projet
/data — fichiers CSV utilisés pour l’analyse
Technologies utilisées
Python
pandas
numpy
matplotlib
seaborn
scikit-learn
nltk
vaderSentiment
