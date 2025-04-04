# 🧠 Introduction au Deep Learning

## 1. Définition du Machine Learning (ML)
Le ML consiste à développer un **modèle prédictif** à partir de données, en utilisant un **algorithme d’optimisation** qui minimise l’erreur entre les prédictions du modèle et les valeurs réelles.

## 2. Types de modèles en ML
- Régression linéaire
- Arbres de décision
- SVM (Support Vector Machines)  
Chaque modèle utilise son propre algorithme d’optimisation.

![image](https://github.com/user-attachments/assets/39169567-56b5-40f5-803b-fb38de95827e)


## 3. Machine Learning vs Deep Learning

| Machine Learning | Deep Learning |
|------------------|---------------|
| Modèles simples (régression, SVM, etc.) | Réseaux de neurones complexes |
| Représentations explicites | Représentation automatique |
| Moins gourmand en données | Requiert beaucoup de données |
| Nécessite l’ingénierie de caractéristiques | Apprend à partir des données brutes |

## 4. Pourquoi le Deep Learning a explosé ?
- Disponibilité de grandes quantités de données
- Amélioration des capacités de calcul (CPU, GPU)
- Algorithmes puissants

## 5. Neurone et perceptron

## 5.1. Motivation 
- Cerveau humain = parallèle, adaptatif, tolérant aux pannes
- Le neurone artificiel imite les fonctions du neurone biologique

## 5.2. Perceptron
- Le perceptron repose sur la plasticité synaptique

  ![image](https://github.com/user-attachments/assets/0d0f40c6-e031-42b5-be5d-cf95db98e07b)

## 5.3 Fonctions d'activations

![image](https://github.com/user-attachments/assets/bea94736-a3a6-49dc-a248-cfaf5b30d0e3)



## 6. Histoire du Deep Learning
### Débuts :
- 1943 : McCulloch & Pitts
- 1949 : Règle de Hebb

### Âge d'or :
- 1957 : Perceptron (Rosenblatt)
- 1960 : ADALINE
- 1969 : Limites du perceptron (Minsky & Papert)

### Renaissance :
- 1982 : Réseaux de Hopfield
- 1986 : Perceptrons multicouches (MLP)
- Depuis 2010s : CNN, LSTM, Transformer...

## 7. Structure d’un réseau de neurones
- Couche d’entrée : données brutes
- Couches cachées : transformations non linéaires
- Couche de sortie : prédiction

![image](https://github.com/user-attachments/assets/a91b52fa-b3d3-4562-a298-4aa823361088)


## 8. Forward Propagation
- Calcul de la sortie via `z = w·x + b` et `a = activation(z)`

![image](https://github.com/user-attachments/assets/7071a315-6794-409e-b1c6-e58f0a8aa4c9)


## 9. Fonction de coût
- MSE pour la régression

![image](https://github.com/user-attachments/assets/b5785094-825f-467f-be6c-4b31e1c6b42a)


- Entropie croisée pour la classification

![image](https://github.com/user-attachments/assets/d1745c40-c334-4a17-b5be-fe90bc9c6d23)


## 10. Backpropagation

Calcul des dérivées (gradients) de la fonction de coût par rapport aux poids

Application de la règle de la chaîne pour chaque couche

Permet de mettre à jour les poids

![image](https://github.com/user-attachments/assets/6ce41d60-10cf-46be-a3ae-836e32264220)


## 11. Descente de Gradient
Principe :
Mise à jour des poids dans la direction opposée au gradient

But : réduire l’erreur

Variantes :
Batch Gradient Descent : mise à jour après tout le dataset

Stochastic Gradient Descent (SGD) : mise à jour après chaque exemple

Mini-batch Gradient Descent : compromis entre les deux
## 12. Apprentissage par époque

- Itération sur tout le dataset
- Apprentissage par observation ou par lot

Initialisation aléatoire des poids

Entrée des données

Propagation avant (calcul de la sortie)

Évaluation de l’erreur

Rétropropagation (calcul des gradients)

Mise à jour des poids

Répéter pour plusieurs époques

## 13. Optimisation de la config ANN
🔧 Paramètres essentiels :

Taux d’apprentissage α : détermine la vitesse de convergence

Dropout : désactive certains neurones pendant l’apprentissage → évite le surapprentissage

Weight Decay : ajoute une pénalité sur les grands poids pour une meilleure généralisation

## 14. Deep Learning Moderne
✅ Fonctions d’activation :
ReLU, Sigmoid, Tanh, Softmax, Leaky ReLU…

✅ Réseaux de neurones convolutifs (CNN)
Utilisés en vision par ordinateur

Extraient automatiquement les caractéristiques spatiales

✅ Réseaux récurrents (RNN / LSTM)
Traitent les données séquentielles (texte, séries temporelles)

✅ Transformer
Utilisé en traitement du langage naturel (ex : GPT, BERT)

Repose sur le mécanisme d’attention

![image](https://github.com/user-attachments/assets/4c8ec325-8626-4112-b97e-6bf668c8e5fc)

