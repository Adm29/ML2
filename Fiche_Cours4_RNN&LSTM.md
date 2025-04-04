# 🧠 Fiche de Cours – Réseaux de Neurones Récurrents (RNN & LSTM)
## 🔁 1. Réseaux de Neurones Récurrents (RNN)
📌 Définition :
Contrairement aux réseaux classiques (feedforward), les RNN traitent des données séquentielles (texte, audio, vidéo).

Le réseau mémorise des états passés pour influencer les prédictions futures.

📦 Architecture :
Chaque cellule RNN prend en entrée l’état caché précédent et l’entrée actuelle.

Sortie à chaque étape : dépend de l’entrée actuelle et de la mémoire (état caché).

Formule d’actualisation :
hₜ = f(hₜ₋₁, xₜ)


![image](https://github.com/user-attachments/assets/53415810-508e-400e-9804-7696f93cb125)


## 📍 2. Applications typiques


![image](https://github.com/user-attachments/assets/c7a6f27e-37d2-4b90-b9be-d45fb040a0d8)

Analyse de sentiments

Traduction automatique

Prédiction de mots

Sous-titrage d’images/vidéos

## ⚠️ 3. Problème du RNN classique : Vanishing Gradient
❌ Problème :
Lors de l'entraînement par rétropropagation, les gradients deviennent trop petits.

Résultat : le réseau oublie les informations lointaines dans une séquence.

## 🔐 4. LSTM – Long Short Term Memory


![image](https://github.com/user-attachments/assets/3ab28d00-9c09-4fe5-aab1-dafa2047197c)


✅ Solution :
Une architecture de RNN équipée de portes de contrôle pour gérer la mémoire à long terme.

Ajoute une nouvelle variable mémoire : cₜ (cell state)


![image](https://github.com/user-attachments/assets/1ab2c992-a4c3-44a2-bafe-63f2a1047d99)


## 🧱 5. Composants du LSTM
1. 🧽 Forget Gate (Porte d’oubli)
Décide quelles informations passées doivent être oubliées

Utilise une sigmoïde pour produire un filtre entre 0 (oubli total) et 1 (mémoire complète)

python
Copier
Modifier
fₜ = σ(Wf · [hₜ₋₁, xₜ] + bf)

![image](https://github.com/user-attachments/assets/f543f44c-5a14-404b-9bf4-86eeff76f1c2)

2. 🟩 Input Gate (Porte d’entrée)
Sélectionne quelles nouvelles informations stocker

Met à jour la mémoire avec de nouvelles données importantes

python
Copier
Modifier
iₜ = σ(Wi · [hₜ₋₁, xₜ] + bi)
c̃ₜ = tanh(Wc · [hₜ₋₁, xₜ] + bc)

![image](https://github.com/user-attachments/assets/0b24dd0f-9bcf-4eef-ab35-0d45c59d22f8)

3. 🔁 Cell State Update
Combine les anciennes informations et les nouvelles :

python
Copier
Modifier
cₜ = fₜ * cₜ₋₁ + iₜ * c̃ₜ
4. 📤 Output Gate (Porte de sortie)
Détermine la sortie de la cellule et le nouvel état caché

python
Copier
Modifier
oₜ = σ(Wo · [hₜ₋₁, xₜ] + bo)
hₜ = oₜ * tanh(cₜ)


![image](https://github.com/user-attachments/assets/46e4eb50-15e4-436b-978f-48ec45a5e089)

## 🧠 Résumé visuel – Fonctionnement du LSTM
vbnet
Copier
Modifier
       Entrée xₜ
           ↓
     ┌────────────┐
     │  Forget     │ → filtre de mémoire passée
     └────────────┘
           ↓
     ┌────────────┐
     │  Input      │ → ajout d'infos utiles
     └────────────┘
           ↓
     ┌────────────┐
     │ Cell state  │ ← mémoire à long terme
     └────────────┘
           ↓
     ┌────────────┐
     │  Output     │ → sortie hₜ
     └────────────┘
