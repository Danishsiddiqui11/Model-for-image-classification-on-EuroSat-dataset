# Model-for-image-classification-on-RGB-EuroSat-dataset 

Keras framework is used to implement this model. As EuroSAT does not define a test set, I used a 80/20 split for train and test. In the [EuroSAT paper](https://arxiv.org/abs/1709.00029) the authors found that the best performing model is **ResNet-50** among the ones they tried so I implemented pre-trained ResNet-50 for this problem.

## Constraints of the current solution:
- **Training.ipynb** performs the data loading and training process.
- For the training I used some of *data augmentations* like random *horizontals flips, shear and zoom range* to increase the diversity of the training data. A pretrained ResNet-50 model was selected with its head replaced as we only have 10 classes. By default only the head is finetuned. 
- After each epoch, the accuracy is computed on the validation set and the best model of the current run is saved in **weights.best.hdf5**.
- The model was trained for ***20 epochs*** and was able to avhieve an accuracy of ***0.96963*** which is close to what was achieved by the authors of EuroSAT paper(0.9857).
- **Inference.ipynb** performs the inference by generating confusion matrix, classification report and sample predictions. It can be seen from the confusion matrix that the classifier sometimes confuses AnnualCrop, as well as the classes PermanentCrop and SeaLake.

## Potential improvements to the solution:

- To make the problem simple only the classifier part of the model was replaced and trained. For increasing the accuracy, the model could be *further fine tuned by freezing the last few layers from the feature extraction layers.*
- Different architectures like *SENet, GoogLENet or ResNet with more number of layers* could be tested for better accuracy. 
- *Changing the activation function* of the classifer could result in slight imrprovement in accuracy.
- Different *Hyperparameter choices* like change in batch size,learning rate, optimizer and number of epochs can be employed to get some improvements.
