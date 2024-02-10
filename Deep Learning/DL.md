- **Steps to Create a Model**:
  1. **Import Libraries**: Import libraries :/
  2. **Define Model Architecture**: Define the number of layers, types of layers (dense, activation functions), and connections between layers.
  3. **Compile Model**: Specify loss function, optimizer (adam,..), and evaluation metrics (accuracy,..).
  4. **Train Model**: Fit the model to the training data.
  5. **Evaluate Model**: Evaluate the model's performance on validation or test data.

### Artificial Neural Networks (ANN):
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

### Convolutional Neural Networks (CNN):
- **Usage**: Widely used in image classification, object detection, and image segmentation tasks.
- **When to Use**: Ideal for tasks involving images or spatial data with hierarchical patterns.
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

### Recurrent Neural Networks (RNN):
- **Usage**: Suitable for tasks like time series prediction, natural language processing, and speech recognition.
- **When to Use**: Ideal for tasks involving sequences where the order of data points matters.
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
