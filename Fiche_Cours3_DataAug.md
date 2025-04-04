# 🧠 Fiche de Cours – Data Augmentation et CNN

## 🔁 1. ImageDataGenerator (Keras)
Classe Keras permettant de :

Charger automatiquement des images

Normaliser les pixels (rescale=1./255)

Appliquer des transformations aléatoires (data augmentation)

📌 Exemple simple :

from tensorflow.keras.preprocessing.image import ImageDataGenerator

datagen = ImageDataGenerator(rescale=1.0/255, validation_split=0.2)
Sans rescale, les pixels sont entre 0 et 255 → apprentissage moins efficace

## 📁 2. flow_from_directory
Permet de :

Charger les images depuis des dossiers

Associer automatiquement chaque image à sa classe

Générer des batchs pour optimiser la mémoire

📂 Organisation du dataset :

dataset/
├── train/
│   ├── Classe1/
│   ├── Classe2/
├── validation/
│   ├── Classe1/
│   ├── Classe2/
Exemple :

train_generator = datagen.flow_from_directory(
    'dataset/train/',
    target_size=(128, 128),
    batch_size=32,
    class_mode='categorical',
    subset='training'
)

## 🧪 3. Data Augmentation
Rend le modèle plus robuste et limite le surapprentissage.

📌 Exemple :

datagen = ImageDataGenerator(
    rescale=1./255,
    rotation_range=20,
    width_shift_range=0.2,
    height_shift_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True
)

## ⚫ 4. Images en niveaux de gris (Grayscale)
Pourquoi ?
Réduction du nombre de paramètres

Utile si la couleur n'est pas informative

Conversion :

datagen = ImageDataGenerator(rescale=1./255, validation_split=0.2)

train_generator = datagen.flow_from_directory(
    'path_to_data/',
    target_size=(128, 128),
    batch_size=32,
    class_mode='categorical',
    color_mode='grayscale'
)
Modification du modèle :

model.add(Conv2D(32, (3, 3), activation='relu', input_shape=(128, 128, 1)))

## 🧱 5. Architecture CNN complète (grayscale)

model = Sequential()
model.add(Conv2D(32, (3, 3), activation='relu', input_shape=(128, 128, 1)))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Conv2D(64, (3, 3), activation='relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Conv2D(128, (3, 3), activation='relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

model.add(Flatten())
model.add(Dense(128, activation='relu'))
model.add(Dense(train_generator.num_classes, activation='softmax'))

## 🖼️ 6. Augmentation avec OpenCV
🔧 Fonctions utiles :
cv2.imread() : charge l'image

cv2.cvtColor(image, cv2.COLOR_BGR2RGB) : conversion pour affichage

cv2.getRotationMatrix2D() + cv2.warpAffine() : rotation

cv2.flip() : effet miroir horizontal ou vertical

cv2.convertScaleAbs() : ajuster contraste/luminosité

cv2.add(image, noise) : bruit gaussien

## 🤖 7. Génération d’images avec GANs
✨ GAN = 2 réseaux :
Générateur : crée de fausses images à partir de bruit

Discriminateur : différencie vraies/fausses images

🧬 Exemple de générateur avec Keras :

from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Reshape, Conv2DTranspose

def build_generator():
    return Sequential([
        Dense(128, activation="relu", input_shape=(100,)),
        Reshape((8, 8, 2)),
        Conv2DTranspose(128, (3,3), strides=(2,2), padding="same", activation="relu"),
        Conv2DTranspose(64, (3,3), strides=(2,2), padding="same", activation="relu"),
        Conv2DTranspose(3, (3,3), strides=(2,2), padding="same", activation="sigmoid")
    ])
💡 Résultat :
Génère une image RGB 64×64

Idéal pour enrichir un dataset avec des images réalistes

