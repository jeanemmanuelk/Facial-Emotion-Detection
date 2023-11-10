
# Facial Emotion Recognition Project

## Objective

This project aims to develop an intelligent facial emotion analysis system that captures and understands real-time emotional states of users from visual cues. It dynamically adapts content (e.g., advertisements, multimedia, user interface elements) to resonate with and enhance the user experience based on their current mood.

## Data Information

The dataset used consists of 48x48 pixel grayscale images of faces, with the faces automatically registered so that the face is more or less centered and occupies about the same amount of space in each image. The categories include Angry, Disgust, Fear, Happy, Sad, Surprise, and Neutral. The training set consists of 28,709 examples, and the public test set consists of 7,178 examples. Data retrieved from Kaggle: [FER2013 Dataset](https://www.kaggle.com/datasets/msambare/fer2013).

## Dependencies

- Python 3
- NumPy
- TensorFlow
- Keras
- Matplotlib

## Setup and Installation

1. Clone the repository.
2. Install the required libraries using `pip install -r requirements.txt`.
3. Download the FER2013 dataset from Kaggle and place it in the `data/` directory.

## Model Architecture

### CNN Model

- Convolutional Neural Network (CNN) with multiple layers, including Conv2D, BatchNormalization, MaxPooling2D, Dropout, Flatten, and Dense layers.
- The model is compiled using Adam optimizer and categorical crossentropy loss function.
- Training is performed with early stopping based on validation loss.

### VGG16 Model (Transfer Learning)

- Utilizes the VGG16 model for feature extraction with added Flatten, Dense, BatchNormalization, and Dropout layers for classification.
- Compiled and trained similarly to the CNN model, with early stopping callbacks.

## Data Preprocessing and Augmentation

- The ImageDataGenerator class from Keras is used for data augmentation, including rescaling, width and height shifting, and horizontal flipping.

## Visualization

- The training process includes visualization of training accuracy vs validation accuracy and training loss vs validation loss.

## Model Evaluation and Saving

- Models are evaluated based on accuracy and loss metrics.
- The best-performing models are saved in the `.h5` format for future use.

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to check [issues page](link-to-issues-page) if you want to contribute.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
