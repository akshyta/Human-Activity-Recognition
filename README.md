# Human-Activity-Recognition

## Motivation and Problem Statement

Human Activity Recognition is an emerging domain in deep learning that has a lot of important applications in daily life including CCTV surveillance and security, Human-Computer Interaction, Health Care Monitoring Systems and more.
Human Activity Recognition is a time-series classification task that essentially involves identification of a person’s actions depicted in a given video like picking something, dropping something etc.

## Related Work

There have been several paradigms proposed in the past for the task of Human Activity Recognition with Video Classification. 
A majority of them involve classification using CNNs. 
2D CNNs are used as classifiers on individual frames and the results are averaged over the frames for final classification. 
3D CNNs are used to capture the static features present in the image and the relationships between the frames thus capturing movement. The results from CNN is then combined using rolling average. 
These use weights pretrained on ImageNet and sport-1m dataset.

## Dataset
Dataset used for the task is  20BN-something-something dataset.  The dataset consists of a large collection of densely-labeled video clips that show humans performing pre defined basic actions with everyday objects. It consists of total 220,847 videos with training set size as 168,913, validation size as 24,777 and test set size as 27,157 and total of 174 labels.
Due to limitations of resources we took only 20 classes of the dataset for the task.
No. of labels = 20
Size of Training Set - 1060
Size of Validation set - 195

## Preprocessing of data
For extracting most relevant information from the video dataset, various preprocessing techniques were tried on the data.
Height, width of each frame and maximum no. of frames captured from the video was varied. Took frame size as 84x84 and frame rate of 5 frames per sec for the final model.
Pixel values for each frame of a  videos were normalized to standard normal zero  mean and unit variance. 
A location was randomly selected and all the frames of a video were randomly cropped at that location. Since this location is different each time the video is read, the model is able to learn at what location the most relevant information is present.
Randomly Flipping of frames of video horizontally and random rotation was done to add more variety to dataset.
Background subtraction on frames of the video was also tried.

## Approach - Exploring Features
Baseline: Trained a 2D convolution network from scratch averaging the output for each frame for the final output.
Final model: Trained a stacked 3D convolution network as a feature extractor combining the static features of frames and capturing the relationship between them using convolution across frame dimension.  The output of feature extractor fed into feature aggregators/classifiers - FC layer, SVM and KNN for prediction using the video embedding.
The non- linear activation used is Relu, in between 3 convolutional filters applying convolution with dilation and padding followed by a fully connected layer.

## Evaluation
Cross-Entropy Loss  		
Accuracy				 
Precision
Recall
F1 score
Top -5 Error

## Design choice
Used 2 2D convolutional layers with max pooling followed by batch-normalization in between them. The output of convolutional layers is combined using 3 fully connected layers. The non-linear activation used is P-Relu.
Used 3 3D convolutional layers with different settings for stride, dilation and padding across the 3 dimensions.    
We had trained all the models for 5 epochs with learning rate 0.001 and optimizer as Adam.  Frame rate was 5 frames per second and frame size was 84 * 84.

## References
The “something something” video database for learning and evaluating visual common sense.
Link: https://arxiv.org/pdf/1706.04261.pdf

CVPR 2014 paper - Large-scale Video Classification with Convolutional Neural Networks
Link:https://www.cv-foundation.org/openaccess/content_cvpr_2014/papers/Karpathy_Large-scale_Video_Classification_2014_CVPR_paper.pdf

Dataset Acquisition: https://20bn.com/datasets/something-something/v2
