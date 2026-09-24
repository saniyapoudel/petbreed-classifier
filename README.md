CNN-Based Pet Breed Classification:
 1. Dataset and Problem 
This project uses the Oxford-IIIT Pet Dataset, an image dataset containing 37 categories of cats and dogs. The objective is to develop a deep-learning image-classification system that can identify the breed/category of a pet from an input image. This is a multi-class image classification problem, where the CNN must select one class from 37 possible categories.

 2. Data Inspection and Preprocessing

The dataset was first inspected by checking the number of images, class names, image dimensions, class distribution, and sample images. The inspection showed that pet images have variations in pose, scale, background, lighting, and orientation, which can make breed classification challenging.

For CNN training, images were resized/cropped to 224 × 224 pixels** and converted into tensors. Image normalization was applied using the standard ImageNet mean and standard deviation, which is particularly appropriate for the pretrained ResNet model. The dataset was divided into **training, validation, and test sets so that the model could be trained, tuned, and finally evaluated on unseen images without data leakage.

 3. Data Augmentation

Training images were augmented using random resized cropping, horizontal flipping, rotation, and color variation. These transformations create realistic variations of the training images and help the model become less dependent on the exact appearance of individual training images. Augmentation was also investigated as an experiment to determine whether it improved generalization.

 4. CNN Architecture and Training

A custom CNN was developed as a baseline model. It contains convolutional layers, batch normalization, ReLU activation, max-pooling, adaptive average pooling, dropout, and fully connected layers. The convolutional layers progressively learn features ranging from simple edges and textures to more complex visual patterns useful for breed classification.

The model was trained using Cross-Entropy Loss and the Adam optimizer. During training, the model performs a forward pass, calculates the loss, performs backpropagation, and updates its weights. Training and validation loss and accuracy were monitored across epochs to identify learning behavior and possible overfitting.

 5. Transfer Learning and Fine-Tuning

In addition to the custom CNN, ResNet18 with pretrained ImageNet weights** was implemented. First, the pretrained layers were frozen and only the final classification layer was trained as a feature extractor. The final layer was replaced to produce predictions for the 37 pet classes.

A second ResNet experiment used fine-tuning, where deeper ResNet layers were unfrozen and trained using a smaller learning rate. This allowed the pretrained visual features to adapt to the specific characteristics of cat and dog breeds in the Oxford-IIIT Pet Dataset.

 6. Experiments and Comparison

Several experiments were performed:

1. Custom CNN with augmentation
2. Custom CNN without augmentation
3. ResNet18 feature extraction
4. ResNet18 fine-tuning

The experiments were compared using validation accuracy, test accuracy, precision, recall, and F1-score. The actual measured results from the experiments are used in the final comparison table rather than estimated values.

 7. Testing and Evaluation

After training, the selected model was evaluated using the independent test dataset. Accuracy measured the overall percentage of correctly classified images, while precision, recall, and F1-score provided more detailed information about classification performance. A confusion matrix was also generated to identify breeds that were frequently confused with one another.

 8. Model Saving and Working Prototype

The final trained model was saved together with the class names, image size, and normalization parameters required for inference. An inference pipeline was created so that a new pet image could be loaded, preprocessed, passed through the trained model, and classified. A simple Gradio GUI was also developed, allowing a user to upload an image and receive the predicted pet breed along with the top prediction probabilities.

 9. Findings and Future Improvement

The experiments provide insight into the effect of CNN architecture, augmentation, transfer learning, and fine-tuning on pet-breed classification. Training and validation curves can be used to identify overfitting, while the confusion matrix shows which breeds are visually difficult to distinguish. Future improvements could include stronger augmentation strategies, hyperparameter tuning, longer controlled training, and experimenting with other pretrained architectures.
