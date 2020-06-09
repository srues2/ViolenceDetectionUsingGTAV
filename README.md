# Violence Detection Using GTA V
There are a small number of studies known about automatic recognizing criminal incidents based on computer science models. Since little to none real data is available due to legal and privacy regulations. A solution to generate datasets is through the use of video gaming data. This thesis has studied the possibilities to recognize criminal incidents with a deep learning framework based on video gaming data. The code on this GitHub page demonstrates the source code of this research.

<!-- TABLE OF CONTENTS -->
## Table of Contents
* [About The Thesis Project](#about-the-thesis-project)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
* [Usage](#usage)
  * [Data pre-processing](#data-pre-processing)
    * [Data preparation](#data-preparation)
    * [Data augmentation](#data-augmentation)
  * [MobileNetSSD CNN model](#mobilenetssd-cnn-model)
  * [3D CNN model](#3d-cnn-model)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)
* [Acknowledgements](#acknowledgements)

<!-- ABOUT THE PROJECT -->
## About The Thesis Project

As mentioned above, the thesis studied how a violent activity will be detected based on a deep learning framework using virtual gaming data. The proposed framework is based on the three-staged end- to-end framework of [Ullah’s research](https://www.semanticscholar.org/paper/Violence-Detection-Using-Spatiotemporal-Features-3D-Ullah-Ullah/953a96b6cf39d9acab182ea6345d0202210ebcc0). The virtual gaming data is a new created dataset based on collected and self-created GTA-V videos. The deep learning framework will be divided into two parts: person identification and violence activity identification. The first part of the framework is to identify persons from the input surveillance videos. A MobileNet-SSD CNN model performs person identification. The MobileNet-SSD CNN model has been based on [Howard's](https://www.semanticscholar.org/paper/MobileNets%3A-Efficient-Convolutional-Neural-Networks-Howard-Zhu/3647d6d0f151dc05626449ee09cc7bce55be497e) research. When a person is identified, the images are passed to a 3D CNN model. The second part of the framework is to identify violence scenarios using the 3D CNN model. This model is trained on virtual gaming data and extract spatiotemporal features. The spatiotemporal features are fed to the Softmax output layer of the 3D CNN model and predict whether or not there is a violent scene in the video. When a violent scenario is discovered, an alert could be sent to the nearest security department or a police station. A visual representation of the deep learning framework is shown in figure 1. 

![Alt text](DLFramework.png)
**Figure 1:**  Deep learning framework of the violent detection method.


<!-- GETTING STARTED -->
## Getting Started
Various software inputs/plugins were used during this project. These software inputs/plugins are required for running the code.

### Prerequisites
The following software / plugins were used during the project:
* [Python](https://www.python.org/downloads/) version 3
* [Opencv](https://opencv.org/opencv-3-4-1/) version 3.4.1
* [Keras](https://keras.io) version 2.2.4
* [TensorFlow](https://www.tensorflow.org/install/pip) version 1.15.2

In addition, we trained and tested the 3D CNN model using a Graphics Processing Unit (GPU). During compiling the model, it turned out that our computers did not have enough CPU and GPU. Therefore, we used a virtual machine on Amazon Web Services (AWS). We employed an EC2 P2.xlarge instance on the AWS server, which comes with an Nvidia k80 GPU and a 61 GB RAM. 


<!-- USAGE EXAMPLES -->
## Usage
This section describes of how the project can be used. The project has passed a number of phases. The first phase consisted of data preparation and data augmentation. The second phase was to create the MobilNetSSD model and conduct the first experiments. Finally, the 3D CNN model was designed and different experiments were performed.

### Data pre-processing
The data pre-processing consists of two parts: 1) data preparation and 2) data augmentation. In the data preparation, frames are extracted from the input videos and the data is prepared to be able to pass through the models. Furthermore, data preparation is performed to further expand the dataset. Next, the data set is split into a train and test data set. 

#### Data preparation
This project collected a GTA-V Fight dataset for people fight pose estimation by exploiting the realistic video game GTA-  V. The videos were collected from YouTube videos and self-created videos from the video game. The input layer of the 3D CNN network expects sequence of frames as inputs. The GTA-V Fight dataset consists of videos and must therefore be converted into sequences of frames. The results of the GTA-V fight dataset were assessed by comparing them with three well-studied datasets for violence recognition. These datasets are called evaluation datasets. 

The file **ViolenceDetectionUsingGTAV/Data_preprocessing/Data_preparation/Preprocessing-GTA-V_dataset.ipynb** contains the pre-processing steps for the GTA-V dataset.

The file **ViolenceDetectionUsingGTAV/Data_preprocessing/Data_preparation/Preprocessing-Evaluation_datasets.ipynb** contains the pre-processing steps for the evaluation datasets.

#### Data augmentation
Data augmentation is applied on the sequences of frames to regularize the data and to prevent overfitting in the model. Two different data augmentation techniques have been applied to the data: a mix of seven traditional augmentation techniques and style augmentation. The code of the style augmentation technique is baded on [Jackson's](https://www.semanticscholar.org/paper/Style-Augmentation%3A-Data-Augmentation-via-Style-Jackson-Abarghouei/a34b1a2cb44cbf647fb64dc9de4c128834bd4cef) research.

The file **ViolenceDetectionUsingGTAV/Data_preprocessing/Data_augmentation/DataAugmentation.ipynb** contains the code for the data augmentation. Both data augmentation techniques are performed in this file.

### MobileNetSSD CNN model
The incoming surveillance sequences were first assessed by a MobileNet-SSD CNN model. This model was originally designed for object detection, fine-grain classification, face attributes and large-scale geolocation. In this thesis, this model was used for person identification. 

Open the folder **"/ViolenceDetectionUsingGTAV/MobilNet_SSD_opencv"** to see the code how people are identified in videos.

The file **"/ViolenceDetectionUsingGTAV/MobilNet_SSD_opencv/RunModelOnVideo.ipynb"** contains the main functions for identifying people in videos.

The file offers two options:
1. You can upload an input video for the person identification model by yourself. As soon as a person is identified in the video, the video stops and the output prints that a person has been identified.
2. You can use your own camera. As soon as a person is identified on the video, a block is created around the person.

### 3D CNN model
Inspired by the performance of [Ullah’s](https://www.semanticscholar.org/paper/Violence-Detection-Using-Spatiotemporal-Features-3D-Ullah-Ullah/953a96b6cf39d9acab182ea6345d0202210ebcc0) network, we decided to use his 3D CNN network to determine the performance of the newly created GTA-V dataset. The network architecture is shown in figure 1.

The file **"ViolenceDetectionUsingGTAV/3D CNN/Generator_NpSequences.ipynb"** contains the code to save the frame sequences in the right input format (numpy files). Then the model is created and evaluated in the file **"ViolenceDetectionUsingGTAV/3D CNN/CreateC3DNetwork_And_TrainingTesting.ipynb"**. After training the model, the best model and weights are stored in the directory **"ViolenceDetectionUsingGTAV/3D CNN/weights"**. Some datasets are too large to be loaded in the AWS GPU server at one time. Therefore, it was decided to split the datasets into several parts. This is done by the code in the file ** **"ViolenceDetectionUsingGTAV/3D CNN/CreateSubdata.ipynb"**.


<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/srues2/ViolenceDetectionUsingGTAV/issues) for a list of proposed features (and known issues).



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.



<!-- CONTACT -->
## Contact

Your Name - [@your_twitter](https://twitter.com/your_username) - email@example.com

Project Link: [https://github.com/your_username/repo_name](https://github.com/your_username/repo_name)



<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
* [Img Shields](https://shields.io)
* [Choose an Open Source License](https://choosealicense.com)
* [GitHub Pages](https://pages.github.com)
* [Animate.css](https://daneden.github.io/animate.css)
* [Loaders.css](https://connoratherton.com/loaders)
* [Slick Carousel](https://kenwheeler.github.io/slick)
* [Smooth Scroll](https://github.com/cferdinandi/smooth-scroll)
* [Sticky Kit](http://leafo.net/sticky-kit)
* [JVectorMap](http://jvectormap.com)
* [Font Awesome](https://fontawesome.com)





<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=flat-square
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=flat-square
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=flat-square
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=flat-square
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=flat-square
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png




## 2. Violence identification
