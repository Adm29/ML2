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

## 📍 2. Applications typiques
Analyse de sentiments

Traduction automatique

Prédiction de mots

Sous-titrage d’images/vidéos

## ⚠️ 3. Problème du RNN classique : Vanishing Gradient
❌ Problème :
Lors de l'entraînement par rétropropagation, les gradients deviennent trop petits.

Résultat : le réseau oublie les informations lointaines dans une séquence.

## 🔐 4. LSTM – Long Short Term Memory
✅ Solution :
Une architecture de RNN équipée de portes de contrôle pour gérer la mémoire à long terme.

Ajoute une nouvelle variable mémoire : cₜ (cell state)

## 🧱 5. Composants du LSTM
1. 🧽 Forget Gate (Porte d’oubli)
Décide quelles informations passées doivent être oubliées

Utilise une sigmoïde pour produire un filtre entre 0 (oubli total) et 1 (mémoire complète)

python
Copier
Modifier
fₜ = σ(Wf · [hₜ₋₁, xₜ] + bf)
2. 🟩 Input Gate (Porte d’entrée)
Sélectionne quelles nouvelles informations stocker

Met à jour la mémoire avec de nouvelles données importantes

python
Copier
Modifier
iₜ = σ(Wi · [hₜ₋₁, xₜ] + bi)
c̃ₜ = tanh(Wc · [hₜ₋₁, xₜ] + bc)
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
