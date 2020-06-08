# ViolenceDetectionUsingGTAV
Violence Detection Using Grand Theft Auto V

# Deep learning framework
The proposed framework is based on the three-staged end- to-end framework of Ullah’s research [16]. The virtual gaming data is a new created dataset based on collected and self-created GTA-V videos. The deep learning framework will be divided into two parts: person identification and violence activity identification. The first part of the framework is to identify persons from the input surveillance videos. A MobileNet-SSD CNN model performs person identification. When a person is identified, the images are passed to a 3D CNN model. The second part of the framework is to identify violence scenarios using the 3D CNN model. This model is trained on virtual gaming data and extract spatiotemporal features. The spatiotemporal features are fed to the Softmax output layer of the 3D CNN model and predict whether or not there is a violent scene in the video. When a violent scenario is discovered, an alert could be sent to the nearest security department or a police station. A visual representation of the deep learning framework is shown in figure 1. 



## 1. Person identification

## 2. Violence identification
