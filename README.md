
# Facial Emotion Recognition Project

## Objective

This project trains and compares two models that classify the emotion shown on a face (seven classes) from a 48x48 grayscale image. The longer-term motivation is systems that react to a user's mood, but this repo only covers the image classification step. It does not include a real-time or content-adapting application.

## Data Information

The dataset used consists of 48x48 pixel grayscale images of faces, with the faces automatically registered so that the face is more or less centered and occupies about the same amount of space in each image. The categories include Angry, Disgust, Fear, Happy, Sad, Surprise, and Neutral. The training set consists of 28,709 examples, and the public test set consists of 7,178 examples. Data retrieved from Kaggle: [FER2013 Dataset](https://www.kaggle.com/datasets/msambare/fer2013).

## Dependencies

- Python 3
- NumPy
- TensorFlow / Keras
- Matplotlib
- OpenCV (only used in the notebook's single-image prediction demo)

## Setup and Installation

1. Clone the repository.
2. Install the libraries listed above (for example `pip install numpy tensorflow matplotlib opencv-python jupyter`). There is no `requirements.txt` yet.
3. Download the FER2013 dataset from Kaggle and extract it so the notebook finds the `archive/train` and `archive/test` folders next to it.

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

## Results

Evaluated once on the 7,178-image public test set:

| Model | Test accuracy | Test loss |
|---|---|---|
| CNN from scratch | 64.6% | 0.990 |
| VGG16 transfer learning | 58.4% | 1.180 |

In this project the smaller CNN trained from scratch did better than the VGG16 model. One possible reason is that FER2013 images are tiny (48x48) grayscale faces, which look very different from the ImageNet photos VGG16 was trained on, but I did not test that. Each model was trained once, and accuracy is the only metric reported, so per-emotion results (for example, which emotions get confused) are not covered here.

## Model Evaluation and Saving

- Models are evaluated based on accuracy and loss metrics.
- The best-performing models are saved in the `.h5` format for future use.

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to check [issues page](https://github.com/jeanemmanuelk/Facial-Emotion-Detection/issues) if you want to contribute.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
