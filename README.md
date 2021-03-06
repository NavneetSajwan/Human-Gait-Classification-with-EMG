# Human Gait Classification using CNNs

Classifying human gait is an imortant task for a bionic feet mechanism. Based on the movement of the person, the artificial feet has to adapt to the situation in real-time. This calls for fast and accurate algorithms to predict the movement of human.

In this project I take up a similar problem.

There are 5 classes for human gait in this problem

1. LG - level ground
2. RA - ramp ascend
3. RD - ramp descend
4. SA - stair ascend
5. SD - stair descend

## DATA
An accelerometer sensor is attached to the human foot. Its data is collected for several steps and for several subjects.

## APPROACH
Machine Learning algoriths like SVM, DECISION TREES and RANDOM FORESTS provided around 95% accuracy on this problem. But, I was curious how deep learning networks, especially CNNs would perform on this data. CNNs being Deep Neural networks are significantly slower than the classical ML algorithms. But, the idea is if they provide sufficient increase in accuracy , then there use can be considered in real-time. Moreover, when CNNs can be used in real time for self-driving cars, with appropriate compute power they sure can be used for real-time gait classification for bionic feet.

First stage was to convert tabular data into images to be fed into a CNN. I used matplotlib to plot the columns.

Here, I came across 2 crucial hyperparameters:

1. Window size
2. Window step size


## Window size

There is a visible repeating pattern in the data. The idea is to choose a window size that covers at least one cycle of this pattern. For me, a window size of 250 samples worked.

## Window step size

A step size greater than the window size would have result in the loss of valuable data. 
A step size smaller than the window size would result in different sections of the cycle ending up in the data. As long as there is visible pattern and sufficient data, a neural network should be able to learn that. But, I preferred to go easy on my network and chose a step size of 250 sample. Thus, effectively taking the similar looking cycle. 

So, now I have 1000 images for each class. Since, there are 5 classes I have a total of 5000 images.

*Below, is a sample image data for our CNN. You can see three plots. Each plot belong to each axis(X, Y, Z) of the accelerometer.*

   ![](images/data_sample.png)
   
Plots of all four classes are different from each other.

*Here, is an example. I have shown 4 of the 5 classes of data here*

   ![](images/four_classes.jpg)
   
## Results

Results are remarkable. It took 6 seconds to train a resnet18 model upto an accuracy of 97 % !

With around 2% increment in accuracy, it can be reported that experiment with CNNs was successful.
