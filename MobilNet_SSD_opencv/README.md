# MobilNet_SSD_opencv
MobilNet-SSD object detection in opencv 3.4.1 and python 2 or 3

The incoming surveillance sequences were first assessed by a MobileNet-SSD CNN model [38]. This model was originally designed for object detection, fine-grain classification, face attributes and large-scale geolocation. In this thesis, this model was used for person identification.

Open the folder "/ViolenceDetectionUsingGTAV/MobilNet_SSD_opencv" to see the code how people are identified in videos.

The file "/ViolenceDetectionUsingGTAV/MobilNet_SSD_opencv/RunModelOnVideo.ipynb" contains the main function for identifying people in videos.

The file offers two options:

You can upload an input video for the person identification model by yourself. As soon as a person is identified in the video, the video stops and the output prints that a person has been identified.
You can use your own camera. As soon as a person is identified on the video, a block is created around the person.


**Mobilenet_ssd_python.py**: 
Example take video file or videocamera as input. 

## Run scripts
```sh
$ python3 mobilenet_ssd_python.py --[params] 
```
If no load params take video input value by default 
