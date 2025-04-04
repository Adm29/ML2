# 🧠 Fiche de Cours : Réseaux de Neurones Convolutifs (CNN)

---

## 📌 Définition générale

Un **CNN** (Convolutional Neural Network) est un réseau de neurones artificiels spécialement conçu pour traiter des données multidimensionnelles comme les images.

Il utilise des **couches convolutionnelles** pour apprendre des **représentations hiérarchiques et spatiales**.

Très performant pour :
- Classification d’images
- Détection d’objets
- Analyse de vidéos

---

## 📦 Structure d’un CNN

- **Couche d’entrée** : données brutes (image sous forme de matrice de pixels)
- **Couches cachées** :
  - Convolution
  - Fonction d’activation (ReLU)
  - Pooling
  - Flattening
  - Fully Connected Layer (FC)
- **Couche de sortie** : prédictions (ex : probabilité des classes)

---

## 🎯 Applications

- **Vision par ordinateur** : reconnaissance faciale, détection d’objets
- **Traitement du langage naturel (NLP)** : classification de texte, analyse de sentiments
- **Audio** : reconnaissance vocale, classification musicale
- **Séries temporelles**

---

## 🧠 Inspiration biologique

Notre cerveau interprète les images en **comblant parfois les vides** → illusions d’optique.

Le CNN imite cette capacité à **extraire des caractéristiques pertinentes** pour classer ou détecter un objet.

---

## 🧮 Représentation d’une image

Une image numérique est une **matrice de pixels** :
- Grayscale = 2D
- Couleur = 3D (R, G, B)

Chaque pixel contient des **valeurs d’intensité**.

---

## ⚙️ Fonctionnement d’un CNN

### 🔹 ÉTAPE 1 : Convolution

- On applique un **filtre (ou kernel)** sur l’image.
- Le filtre (ex : 3×3) glisse sur l’image et effectue un **produit scalaire local**.
- Résultat : **carte de caractéristiques**.
- Plusieurs filtres = plusieurs cartes.

**🔸 Problème :** perte d’informations → on y remédie en laissant le réseau **apprendre les bons filtres**.

---

### 🔹 ÉTAPE 1' : Activation ReLU

- Fonction : `ReLU(x) = max(0, x)`
- Supprime les **valeurs négatives** dans les cartes convoluées.
- Apporte de la **non-linéarité**, indispensable pour traiter des images complexes.

---

### 🔹 ÉTAPE 2 : Pooling (Sous-échantillonnage)

**But** : réduire la taille des cartes tout en conservant les informations essentielles.

#### 🔸 Types :
- **Max Pooling** (le plus utilisé) : conserve la valeur maximale.
- **Average Pooling** : moyenne des valeurs.
- **Global Pooling** : une seule valeur par carte.
- **Sum Pooling** : somme des valeurs.

#### 🧩 Avantages :
- Moins de paramètres à apprendre
- Moins de surapprentissage
- Robustesse aux variations de position

---

### 🔹 Padding (complément important)

Technique qui **ajoute des zéros autour de l’image** pour **préserver sa taille** après convolution.

Utile pour **éviter de perdre des bords**.

---

### 🔹 ÉTAPE 3 : Flattening

Transformation des **cartes de caractéristiques** (matrices) en **vecteur plat**.

→ Prêt pour être connecté à une **couche entièrement connectée**.

---

### 🔹 ÉTAPE 4 : Fully Connected Layer (FC)

- Le vecteur est connecté à un ou plusieurs **neurones classiques**.
- Dernière couche = **sortie du modèle** (probabilités, scores, etc.)

---

## 🧠 Résumé global du processus CNN

| Étape            | Description                     |
|------------------|----------------------------------|
| **Convolution**  | Extraction des caractéristiques |
| **ReLU**         | Activation non-linéaire         |
| **Pooling**      | Réduction de dimensions         |
| **Flattening**   | Mise à plat des données         |
| **Fully Connected** | Prédiction (ex : Softmax)    |
