### Steps to Create a Model:
  1. **Import Libraries**: Import libraries :/
  2. **Define Model Architecture**: Define the number of layers, types of layers (dense, activation functions), and connections between layers.
  3. **Compile Model**: Specify loss function, optimizer (adam,..), and evaluation metrics (accuracy,..).
  4. **Train Model**: Fit the model to the training data.
  5. **Evaluate Model**: Evaluate the model's performance on validation or test data.

## Artificial Neural Networks (ANN):
- **Usage**: Used for classification, regression, and pattern recognition.
- **When to Use**: when we have structured data and when feature extraction is an important stepp.
- **Most Important Code Part**:
  - Defining the model architecture:
    ```python
    model = Sequential([
        Dense(units=128, activation='relu', input_shape=(input_shape,)),
        Dense(units=num_classes, activation='softmax')
    ])
    ```

---

## Things to Keep in Mind:

### Softmax:
- The activation function decides whether a neuron should be activated or not.
- for multi class classification task.
- **Input**: Vector of arbitrary real-valued scores (logits).
- **Output**: Probability distribution over multiple classes.

### Sigmoid:
- The activation function determines whether a neuron should be activated or not.
- for binary classification task.
- **Input**: Scalar or vector.
- **Output**: Probability in the range [0, 1].

### Tanh:
- Similar to the sigmoid function
- **Input**: Scalar or vector.
- **Output**: between -1 and 1.

---

## Convolutional Neural Networks (CNN):
- **Usage**: Widely used in image classification, object detection, and image segmentation tasks.
- **When to Use**: When we have images or hierarchical patterns.
- **Most Important Code Part**:
  - Defining the convolutional layers:
    ```python
    model = Sequential([
        Conv2D(32, kernel_size=(3, 3), activation='relu', input_shape=input_shape),
        MaxPooling2D(pool_size=(2, 2)),
        Flatten(),
        Dense(128, activation='relu'),
        Dense(num_classes, activation='softmax')
    ])
    ```
---

## Things to Keep in Mind:

### Convolutional Layers:
  - Conv2D: Applies convolutional operation with 32 filters and a kernel size of (3, 3).
  - Activation: ReLU activation function is applied to introduce non-linearity.
  - Input Shape: Specifies the input shape of the data.
  
### Pooling Layer:
  - MaxPooling2D: Performs max pooling operation with a pool size of (2, 2).

### Flattening Layer:
  - Flatten: Reshapes the output of the convolutional layers into a 1D vector.

### Dense Layers:
  - Dense: Fully connected layer with 128 units.
  - Activation: ReLU activation function is applied.
  
### Output Layer:
  - Dense: Fully connected layer with the number of units equal to the number of classes.
  - Activation: Softmax activation function is applied for multi-class classification tasks.

---

## Recurrent Neural Networks (RNN):
- **Usage**: Suitable for tasks like time series prediction, natural language processing, and speech recognition.
- **When to Use**: When we have sequences where the order of data points matters (eg: text completion, sentiment analysis, time series prediction).
- **Most Important Code Part**:
  - Defining an LSTM layer:
    ```python
    model = Sequential([
        LSTM(128, input_shape=(timesteps, features)),
        Dense(num_classes, activation='softmax')
    ])
    ```

### Saving Models:
- In TensorFlow/Keras, you can save models using the `save()` method:
  ```python
  model.save('model_name.h5')
  ```
- To load the saved model:
  ```python
  from tensorflow.keras.models import load_model
  loaded_model = load_model('model_name.h5')
  ```
  
- To convert the ".h5" to ".tflite":
  ```python
  import tensorflow as tf

  converter = tf.lite.TFLiteConverter.from_keras_model(model)
  tflite_model = converter.convert()
  
  with open('model.tflite', 'wb') as f:
    f.write(tflite_model)
  ```

	

### Summary:
- **ANN**: General purpose neural network architecture for structured data.
- **CNN**: Specialized for image data.
- **RNN**: Designed for sequential data (voice, text,...).

-----

## Troubleshooting Model Performance:

1. **Adjust Hyperparameters (optimizer, batch size, number of epochs, learning rate, activation functions, loss functions...)**
2. **Evaluate Data Quality**
3. **Feature Engineering**
4. **Regularization (Dropout)**
5. **Data Augmentation**
6. **Change Algorithm**

## Supervised Learning Algorithms:
- Artificial Neural Network (ANN)
- Convolutional Neural Network (CNN)
- Recurrent Neural Network (RNN)
- Linear Regression
- Logistic Regression
- Decision Tree
- Random Forest

## Unsupervised Learning Algorithms:
- K-means
- Apriori Algorithm
- Principal Component Analysis (PCA)
- Dimensionality Reduction

## Usage of some Parameters:

1. **Batch Size**: Number of training examples used in one iteration.
   ```python
   batch_size = 32
   ```

2. **Epoch**: One pass through the entire training dataset.
   ```python
   epochs = 10
   ```

3. **Learning Rate**: Step size for model learning.
   ```python
   learning_rate = 0.001
   ```

4. **Optimizer**: Algorithm adjusting model parameters.
   ```python
   optimizer = tf.keras.optimizers.Adam(learning_rate=0.001)
   ```

5. **Loss Function**: Measures difference between predicted and actual values.
   ```python
   loss = 'sparse_categorical_crossentropy'
   ```

6. **Activation Function**: Applies non-linearity to neuron outputs.
   ```python
   activation = 'relu'
   ```

7. **Units/Neurons**: Number of nodes in a layer.
   ```python
   units = 128
   ```

8. **Dropout**: Regularizes model by ignoring random neurons.
   ```python
   dropout_rate = 0.2
   ```

9. **Validation Split**: Proportion of training data for validation.
   ```python
   validation_split = 0.2
   ```

10. **Early Stopping**: Stops training if validation performance worsens.
    ```python
    early_stopping_callback = tf.keras.callbacks.EarlyStopping(monitor='val_loss', patience=3)
    ```
