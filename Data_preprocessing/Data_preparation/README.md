# Data Preparation
This project collected a GTA-V Fight dataset for people fight pose estimation by exploiting the realistic video game GTA- V. The videos were collected from YouTube videos and self-created videos from the video game. The input layer of the 3D CNN network expects sequence of frames as inputs. The GTA-V Fight dataset consists of videos and must therefore be converted into sequences of frames. The results of the GTA-V fight dataset were assessed by comparing them with three well-studied datasets for violence recognition. These datasets are called evaluation datasets.

## Data pre-processing GTA-V dataset
The file **"ViolenceDetectionUsingGTAV/Data_preprocessing/Data_preparation/Preprocessing-GTA-V_dataset.ipynb"** contains the pre-processing steps for the GTA-V dataset.

The input layer of the 3D CNN network expects sequence of frames as inputs. The GTA-V Fight dataset consists of videos and must therefore be converted into sequences of frames. The frames of each video are extracted with a rate of 25 frames per second. The frame names are formatted as “video_folder/%06d.jpg”. Then the video frames are resized into 112x112 pixels. The next step is to convert the frames of each video to sequences of 16 frames. During the generation of these sequences is taken into account an 8-frame overlap between two sequences. The main advantage is that there is less information loss between two sequences. In addition, more sequence data is generated which leads to more data regularization.

In the pre-processing step described above, the sequences are only created and the paths of the sequences are stored in a text file. The actual generation of the sequences is done in the **"ViolenceDetectionUsingGTAV/3D CNN/Generator_NpSequences.ipynb"** file. Below is an example of how the sequence paths are stored: 

*..*
*/Volumes/LogisP/Videos/GTA/NoViolence_Frames/22-WalkingFront 9 0 25 \*
*/Volumes/LogisP/Videos/GTA/NoViolence_Frames/69-WorkoutMen3 25 0 69 \*
*/Volumes/LogisP/Videos/GTA/Violence_Frames/Fight-63 89 1 190 \*
*..*

Each line of code represents a sequence. In the example above are thus displayed three sequences.
The first part of the code represents the path where the frames of a video are stored.


## Data pre-processing evaluation datasets
The file **"ViolenceDetectionUsingGTAV/Data_preprocessing/Data_preparation/Preprocessing-Evaluation_datasets.ipynb"** contains the pre-processing steps for the evaluation datasets.

