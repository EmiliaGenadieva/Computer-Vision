# Computer-Vision
## Identify human expressions such as happiness and sadness.
Explore ways to detect more complex emotions.
# Context
An important global firm receives thousands of job applications every year. However, the HR team does not have enough time to review each one of the applications. This is the reason why they are looking for innovative solutions to be integrated into the selection and recruitment process.<br/>
Looking to accelerate the interview pace, the company is investing resources in a video-interview system where pre-defined questions are asked by a virtual HR agent. In some jobs, personality is an important asset and the company would like to automatically analyze the images from the video footage, quantify the emotions expressed by the job applicants, and select the appropriate candidate according to the open job opportunities. They want to take it a step further, detecting a smile or sad face is not enough. They want a tool capable of recognizing even subtle changes in facial expression that might indicate a particular emotion.
# Objective
### Recognize sadness and happiness in images
As a minimum requirement of the effectiveness of the model is the ability of the model to recognize if the emotion is positive ( happy ) or negative ( sad ). Also defined could be neutral with other categories.
### Recognize more complex emotions in images
As we could find some images which are already classified in 7 classes, the task left was only to train a model with more
# Dataset
Although human faces are a frequently found on the internet, there a many regulations where is it not allowed to use someone's photo without permission, still for educational purposes a dataset open to be used for educational purposes could be found on Kaggle.
[FER-2013](https://www.kaggle.com/datasets/msambare/fer2013)</br>
[Natural Human Face Images](https://www.kaggle.com/datasets/sudarshanvaidya/random-images-for-face-emotion-recognition)</br>
The FER dataset has 35 000 images divided into 7 categories. Found on Kaggle were similar gray images. They were added to the corresponding categories, in total there were 42 000 images to fine-tune the model.</br>
The train data has 34267 images belonging to 7 classes. The test data contains 7178 images belonging to 7 classes.
# Prerequisites
>Installation of tensorflow library. Download of the model which is suitable for evaluation of images.
>First the data is being analysed and the images are checked for common anomalies like bad image quality, missing photo, unrecognisable posture etc. Once the dataset is finalised, it is loaded from the data folder. The training of the model is performed locally on the computer or on Google Colab. Both times is used a notebook where the different steps are run separately. This approach allows more flexibility to adjust and observe in real time if some errors raise.<br>
The trained model is saved to Google Drive or locally on the computer.</br>
The pretrained model is loaded and evaluated on several test photos. Some charts
### Established baseline model
[Keras models](https://keras.io/api/applications/)</br>
The best prebuild models used were <b>ResNet50, VGG19, MobileNetV2</b>. The chosen model is VGG19, as it gave the best results afterwards. </br>
By loading the base model, we specify the input shape of our images. The dataset has grey image with a size of 48 to 48. There is no use to load a bigger size from the base model, so we load also (48 x 48 x 3). We specify also 3 colors even if our images use 1 channel black-white.
We could also obtain good results by building a model from scratch by defining some layers. The accuracy obtained was <b>74.8% on the train set</b>
The steps taken by building the model twice. Both times we take dataset but the 2nd time some weights from the base model are taken, the rest of the weights are frozen by setting trainable = False for these layers of the prebuild Keras model. 
###  Metrics to evaluate the model
Mostly used is the loss, accuracy and presition f1 score. Confusion matrix shows the metrics per emotion category.
Precision is the number of true positives (TP) over the number of true positives plus the number of false positives (FP).
Each time we build the model, observed is a very high Presition - above 78%, which gives hopes that the future predictions of the model will be accurate.
#### Callbacks
* LossAndErrorPrintingCallback(keras.callbacks.Callback)
By defining a custom callback additional metrics can be specified. The printed output per epoch shows the evolution of the loss, val_accuracy and precision.
* This metric gives the possibility to stop the building process of the model earlier. If the model shows no more improvements, the building of the model will be stopped. If 'training loop will check at end of every epoch whether the loss is no longer decreasing, considering the min_delta and patience if applicable. Once it's found no longer decreasing, model.stop_training is marked True and the training terminates.'
* ReduceLROnPlateau
By the utilisation of this functionality the building of the model is dynamically adjusted. The learining rate of the optimiser is decreased or increased while building.
Last 2 metrics will take into consideration the val_accuracy as we are interested in the performance of the model with unseen data.

# Time Frame
Type of Challenge: Learning</br>
Duration: 8 days</br>
Development Deadline: 11/05/2023 4:30 PM</br>
Repo Deadline: 12/05/2023 4:00 PM</br>
Challenge: Individual (or Team)
