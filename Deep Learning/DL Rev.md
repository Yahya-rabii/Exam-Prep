# Deep learning exam preparation :


# les Etapes d'apprentissage en profondeur : 
  
    ```

    1. Dataset
    2. Model
    3. learning and training
    4. Testing and Deployment

    ```


------------------------------------------------------------

# Les bibliothèques de Deep Learning :

- keras : est une bibliothèque open source qui fournit une interface Python pour l'apprentissage en profondeur. 


- Tensorflow : est une bibliothèque open source pour l'apprentissage automatique développée par Google.


- matprotlib : est une bibliothèque de traçage 2D en Python qui produit des chiffres de qualité de publication dans une variété de formats imprimables et interactifs à travers les plates-formes.


- numpy : est une bibliothèque pour le langage de programmation Python, ajoutant un support pour les tableaux multidimensionnels et les matrices, ainsi que des fonctions mathématiques pour travailler avec ces tableaux.


- pandas : est une bibliothèque logicielle écrite pour le langage de programmation Python pour la manipulation et l'analyse des données.


- scikit-learn : est une bibliothèque python open source qui fournit des outils simples et efficaces pour l'analyse prédictive des données.


- streamlit : est une bibliothèque open-source Python qui facilite la création d'applications web pour l'analyse de données, la visualisation de données et la création de tableaux de bord interactifs.


------------------------------------------------------------

# Les types de réseaux de neurones : 

    - ANN (Artificial Neural Network - Réseau de Neurones Artificiels) : Modèle classique de réseaux de neurones organisés en couches pour diverses tâches de classification et de régression.

    - CNN (Convolutional Neural Network - Réseau de Neurones Convolutifs) : Spécialement conçu pour le traitement d'images, avec des couches de convolution pour extraire les caractéristiques et des couches de regroupement pour réduire la dimensionnalité.

    - RNN (Recurrent Neural Network - Réseau de Neurones Récursifs) : Adapté au traitement de données séquentielles grâce à des connexions récurrentes permettant de conserver une mémoire interne, utilisé pour la traduction automatique, la génération de texte, etc.

      - LSTM (Long Short-Term Memory) : Un type de RNN qui est capable de conserver des informations sur de longues séquences de données, souvent utilisé pour des tâches de traitement du langage naturel.



------------------------------------------------------------

# les modèles de langage :

- LLM (large language model) : est un modèle de langage qui est capable de générer du texte de manière autonome (GPT 3).

- pre trained model : est un modèle qui a été formé sur une tâche avant d'être utilisé pour une autre tâche.

- GPT : est un modèle de langage pré-entraîné qui a été formé sur un très grand corpus de texte pour prédire le mot suivant dans une séquence de mots.


------------------------------------------------------------

# les types d'apprentissage : 

    - Supervised Learning : Apprentissage supervisé, où le modèle est entraîné sur un ensemble de données étiqueté, c'est-à-dire que les entrées sont associées à des sorties attendues.

    - Unsupervised Learning : Apprentissage non supervisé, où le modèle est entraîné sur un ensemble de données non étiqueté, c'est-à-dire que les entrées ne sont pas associées à des sorties attendues.

    - Reinforcement Learning : Apprentissage par renforcement, où le modèle apprend à prendre des décisions en interagissant avec un environnement, en recevant des récompenses ou des pénalités pour ses actions.


------------------------------------------------------------

# les types de problèmes : 

    - Classification : Tâche consistant à prédire une étiquette discrète pour une entrée donnée, par exemple, prédire si une image contient un chat ou un chien.

    - Regression : Tâche consistant à prédire une valeur continue pour une entrée donnée, par exemple, prédire le prix d'une maison en fonction de ses caractéristiques.

    - Clustering : Tâche consistant à regrouper des entrées similaires dans des groupes, par exemple, regrouper des clients en fonction de leurs comportements d'achat.

    - Anomaly Detection : Tâche consistant à identifier des entrées qui sont significativement différentes du reste, par exemple, détecter des transactions frauduleuses dans un ensemble de transactions.



------------------------------------------------------------

# les types de couches : 

    - Dense : Couche entièrement connectée, où chaque neurone est connecté à chaque neurone de la couche précédente.

    - Conv2D : Couche de convolution 2D, utilisée pour extraire des caractéristiques des images.

    - MaxPooling2D : Couche de regroupement maximale 2D, utilisée pour réduire la dimensionnalité des images.

    - Flatten : Couche de mise à plat, utilisée pour convertir les sorties des couches de convolution en un vecteur pour les couches entièrement connectées.

    - LSTM : Couche de mémoire à court et long terme, utilisée pour traiter des données séquentielles.

    - Dropout : Couche de régularisation, utilisée pour réduire le surajustement en désactivant aléatoirement certains neurones pendant l'entraînement.

    - BatchNormalization : Couche de normalisation par lots, utilisée pour accélérer l'entraînement et réduire le surajustement en normalisant les entrées de chaque mini-lot.


------------------------------------------------------------


# les types de fonctions d'activation : 

    - Sigmoid : Fonction d'activation qui produit une sortie dans la plage [0, 1], utilisée pour les tâches de classification binaire.

    - ReLU (Rectified Linear Unit) : Fonction d'activation qui produit une sortie dans la plage [0, inf], utilisée pour introduire de la non-linéarité dans les réseaux de neurones.

    - Softmax : Fonction d'activation qui produit une distribution de probabilité sur un ensemble de classes, utilisée pour les tâches de classification multi-classe.

    - Tanh : Fonction d'activation qui produit une sortie dans la plage [-1, 1], utilisée pour introduire de la non-linéarité dans les réseaux de neurones.


------------------------------------------------------------





# les types d'optimiseurs : 

    - Adam : Optimiseur qui adapte le taux d'apprentissage pour chaque paramètre du modèle en fonction des estimations des moments du premier et du deuxième ordre du gradient.


------------------------------------------------------------


# les types de prétraitement des données : 

    - Normalization : Mise à l'échelle des valeurs des caractéristiques pour qu'elles se situent dans une plage spécifique, par exemple [0, 1].

    - Standardization : Mise à l'échelle des valeurs des caractéristiques pour qu'elles aient une moyenne nulle et un écart type unitaire.

    - One-Hot Encoding : Encodage des variables catégorielles en vecteurs binaires pour les utiliser dans les modèles d'apprentissage automatique.

    - Tokenization : Conversion de texte en une séquence de jetons, par exemple des mots ou des sous-chaînes de caractères.

    - Padding : Ajout de zéros ou de valeurs spécifiques pour remplir les séquences à une longueur spécifique.

  ------------------------------------------------------------


#  Convolutional Neural Network (CNN):

```python
        import tensorflow as tf

        # Define a simple CNN model
        model = tf.keras.Sequential([
            tf.keras.layers.Conv2D(32, (3, 3), activation='relu', input_shape=(28, 28, 1)),
            tf.keras.layers.MaxPooling2D((2, 2)),
            tf.keras.layers.Flatten(),
            tf.keras.layers.Dense(10, activation='softmax')
        ])

        # Compile the model
        model.compile(optimizer='adam',
                    loss='sparse_categorical_crossentropy',
                    metrics=['accuracy'])

        # Train the model
        model.fit(x_train, y_train, epochs=5)
```


# Recurrent Neural Network (RNN):

```python
        

import tensorflow as tf

# Define a simple RNN model
model = tf.keras.Sequential([
    tf.keras.layers.SimpleRNN(10, input_shape=(None, 1)),
    tf.keras.layers.Dense(10, activation='softmax')
])

# Compile the model
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# Train the model
model.fit(x_train, y_train, epochs=5)


```


#    Artificial Neural Network (ANN):

```python

import tensorflow as tf

# Define a simple ANN model
model = tf.keras.Sequential([
    tf.keras.layers.Flatten(input_shape=(28, 28)),
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dense(10, activation='softmax')
])

# Compile the model
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# Train the model
model.fit(x_train, y_train, epochs=5)


```


#    Long Short-Term Memory (LSTM):


```python

import tensorflow as tf

# Define a simple LSTM model
model = tf.keras.Sequential([
    tf.keras.layers.LSTM(10, input_shape=(None, 1)),
    tf.keras.layers.Dense(10, activation='softmax')
])

# Compile the model
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# Train the model
model.fit(x_train, y_train, epochs=5)


```


#     K-Nearest Neighbors (KNN):

```python

from sklearn.neighbors import KNeighborsClassifier

# Create a KNN classifier
knn = KNeighborsClassifier(n_neighbors=5)

# Train the classifier
knn.fit(X_train, y_train)

# Make predictions
predictions = knn.predict(X_test)


```







    ------------------------------------------------------------

