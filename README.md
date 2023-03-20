# Model-for-image-classification-on-EuroSat-dataset

Keras framework is used to implement this model.As EuroSAT does not define a test set, I used a 90/10 split for train and test. In the EuroSAT paper the authors found that the best performing model is ResNet-50 among the ones they tried so I implemented pre-trained ResNet-50 for this problem.

# Constraints of the current solution:
Training.ipynb performs the data loading and training process

For the training I used some of data augmentations like random horizontals flips, shear and zoom range to increase the diversity of the training data. A pretrained resnet50 model was selected with its head replaced as we only have 10 classes. By default only the head is finetuned. 
After each epoch, the accuracy is computed on the validation set and the best model of the current run is saved in weights.best.hdf5
The model was trained for 20 epochs and was able to avhieve an accuracy of 0.96963 which is close to what was achieved by the authors of EuroSAT paper(0.9857)
