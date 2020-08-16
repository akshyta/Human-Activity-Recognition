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
