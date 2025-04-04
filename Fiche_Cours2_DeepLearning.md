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

![image](https://github.com/user-attachments/assets/e41049d7-89be-4399-9815-0f09f2f21512)


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

![image](https://github.com/user-attachments/assets/811eccff-4908-4e38-b83a-6eb0a9a00a05)


Une image numérique est une **matrice de pixels** :
- Grayscale = 2D
- Couleur = 3D (R, G, B)

Chaque pixel contient des **valeurs d’intensité**.

![image](https://github.com/user-attachments/assets/c8b9363f-f77d-4199-b67c-ffe2dc447855)

---

## ⚙️ Fonctionnement d’un CNN

![image](https://github.com/user-attachments/assets/b395a95b-386d-4d90-9e8a-c81856622e43)


### 🔹 ÉTAPE 1 : Convolution

![image](https://github.com/user-attachments/assets/92ef7c55-7b96-437d-bc5c-ae484b4abf0d)


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

![image](https://github.com/user-attachments/assets/bf6509f5-c900-4376-9ba2-86c77069554c)


#### 🧩 Avantages :
- Moins de paramètres à apprendre
- Moins de surapprentissage
- Robustesse aux variations de position

---

### 🔹 Padding (complément important)

Technique qui **ajoute des zéros autour de l’image** pour **préserver sa taille** après convolution.

Utile pour **éviter de perdre des bords**.

![image](https://github.com/user-attachments/assets/6408cd33-9b5f-4f0b-9a9b-49101b11a7e0)


---

### 🔹 ÉTAPE 3 : Flattening

Transformation des **cartes de caractéristiques** (matrices) en **vecteur plat**.

→ Prêt pour être connecté à une **couche entièrement connectée**.

![image](https://github.com/user-attachments/assets/ee51fe24-10d6-45c6-93e6-108b60bf4fd1)


---

### 🔹 ÉTAPE 4 : Fully Connected Layer (FC)

- Le vecteur est connecté à un ou plusieurs **neurones classiques**.
- Dernière couche = **sortie du modèle** (probabilités, scores, etc.)



![image](https://github.com/user-attachments/assets/e72089bc-3a8a-4930-aed6-cc26c4bd1206)

---

## 🧠 Résumé global du processus CNN

| Étape            | Description                     |
|------------------|----------------------------------|
| **Convolution**  | Extraction des caractéristiques |
| **ReLU**         | Activation non-linéaire         |
| **Pooling**      | Réduction de dimensions         |
| **Flattening**   | Mise à plat des données         |
| **Fully Connected** | Prédiction (ex : Softmax)    |
