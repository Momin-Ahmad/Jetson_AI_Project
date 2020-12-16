# Jetson_AI_Project
## PyTorch based classifier deployed on Jetson Nano
### Description
This is a repository containing the files used in my Jetson AI project. I have used NVIDIAs Jetson Nano (4 GB version). The environment setup on Nano was done using the OS file provided by NVIDIA, https://developer.nvidia.com/jetson-nano-sd-card-image. Once downloaded, this OS is burnt onto an SD card. This SD card is plugged into the Nano and we have our Ubuntu system ready on the Nano. Along with Ubuntu, there are many packages installed. However, for my project, I had to install PyTorch v1.7. In addition to this, I required packages like pandas for file manipulation. I installed it after following the steps from https://forums.developer.nvidia.com/t/pytorch-for-jetson-version-1-7-0-now-available/72048. For hardware setup, I followed JetsonHacks(https://www.youtube.com/channel/UCQs0lwV6E4p7LQaGJ6fgy5Q).
### Training
The Plant_pathology_train file consists of the transfer learning code which i deployed on Google Colab's GPU. The training consists of 1821 images. The dataset is downloaded from Kaggle's Plant Pathology competition https://www.kaggle.com/c/plant-pathology-2020-fgvc7/data. The data is in raw form and to convert it into ImageNet format, I wrote a preprocessing script which is also included in the repository. The model I used is a pretrained resnet18, modified for 4 output classes. After training for 10 epochs, I get 93% accuracy.
![](Train.Jpg)
### Testing
After obtaining the trained model from training, I saved it and transferred it to Jetson Nano. There, I ran the JetsonTest.py file which took the pretrained model weights and test images as input and gave me as output, a csv file containing class probabilities for each test image. After uploading my csv file to kaggle, I obtained 88% test accuracy.
![](Test%20Result.jpeg)
