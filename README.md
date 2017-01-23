# Behavioural Cloning

# Preprocessing
* Data was cropped to include only the road ignoring other parts of the background while also being transform from RGB to YUV. The image is also resized to be the same dimensions as the images in the Nvidia end-to-end system(https://images.nvidia.com/content/tegra/automotive/images/2016/solutions/pdf/end-to-end-dl-using-px.pdf).

# Data Augmentation/Generation
* I found that the best approach to getting the car to drive successfully was by using different aumentation techinques to create additional data. The augmentation techniques included flipping, xy translating, and using the left/right images. The steering angles were all changed accordingly.

* The data is not all loaded into memory at once, they are loaded as needed. The generator "batch_generator" genreates data based on the batch size and each data augmentaion is done with some probability in the generator. 

# Network Architecture
* Experiments were conducted to choose the best architecture for this problem. Initially I had used my model from project 2 as a baseline afterwards I tired different transfer learning approaches by using GoogLeNet/Alexnet. In the end the architecture that worked best on my validation set and on the track was the architecture used in the end-to-end system developed by Nvidia. The network consist of static normalization layer -> 5 convolutional layers -> 4 full connected layers illustrated below:

![alt tag](https://github.com/SyedAzizEnam/CarND-Project3/blob/master/Screen%20Shot%202017-01-17%20at%2010.46.18%20PM.png)

# Training
* To train the model I start by splitting the data into training and validation sets. I then used an Adam optimizer and used MSE as the loss.
