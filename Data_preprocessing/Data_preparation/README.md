# Data Preparation
This project collected a GTA-V Fight dataset for people fight pose estimation by exploiting the realistic video game GTA- V. The videos were collected from YouTube videos and self-created videos from the video game. The input layer of the 3D CNN network expects sequence of frames as inputs. The GTA-V Fight dataset consists of videos and must therefore be converted into sequences of frames. The results of the GTA-V fight dataset were assessed by comparing them with three well-studied datasets for violence recognition. These datasets are called evaluation datasets.

## Data pre-processing GTA-V dataset
The file **"ViolenceDetectionUsingGTAV/Data_preprocessing/Data_preparation/Preprocessing-GTA-V_dataset.ipynb"** contains the pre-processing steps for the GTA-V dataset.

The input layer of the 3D CNN network expects sequence of frames as inputs. The GTA-V Fight dataset consists of videos and must therefore be converted into sequences of frames. The frames of each video are extracted with a rate of 25 frames per second. The frame names are formatted as “video_folder/%06d.jpg”. Then the video frames are resized into 112x112 pixels. The next step is to convert the frames of each video to sequences of 16 frames. During the generation of these sequences is taken into account an 8-frame overlap between two sequences. The main advantage is that there is less information loss between two sequences. In addition, more sequence data is generated which leads to more data regularization.

In the pre-processing step described above, the sequences are only created and the paths of the sequences are stored in a text file. The actual generation of the sequences is done in the **"ViolenceDetectionUsingGTAV/3D CNN/Generator_NpSequences.ipynb"** file. Each line has the following format:

<string_path> <starting_frame> <label> <group_number>

Below is an example of how the sequence paths are stored: 

*/Volumes/LogisP/Videos/GTA/NoViolence_Frames/22-WalkingFront 9 0 25*
*/Volumes/LogisP/Videos/GTA/NoViolence_Frames/69-WorkoutMen3 25 0 69*
*/Volumes/LogisP/Videos/GTA/Violence_Frames/Fight-63 89 1 190*

Each line of code represents a sequence. So in the example above, three sequences are shown. The first sequence is used as an example to explain the rule.
* */Volumes/LogisP/Videos/GTA/NoViolence_Frames/22-WalkingFront:*
The first part of the code represents the path where the frames of a video are stored.
* *9:*
This is the starting frame number of the sequence. The <starting_frame> is used to specify the starting frame of the clip. We note that 3D CNN extract features of 16-frame-long videos. For example, if starting frame is 1, then you are extracting features for the clip (from the video specified by <string_path>) from frame 1 to 16. If starting frame is 9, then the clip of interest is from frame 9 to 24. 
* *0:*
This is the label of the sequence. If a sequence is labeled 0, it does not contain violence scenarios. If the sequence has a label 1, the sequence contains violence situations.
* *25:*
This is the group number of the sequence. All sequences generated from the same video have the same group number. This group number has been added for the stratified split. A stratified split was applied based on the number of occurrences of violence situations. When splitting the sequence data, it was taken into account that sequences from the same video were in the same subset.

## Data pre-processing evaluation datasets
The file **"ViolenceDetectionUsingGTAV/Data_preprocessing/Data_preparation/Preprocessing-Evaluation_datasets.ipynb"** contains the pre-processing steps for the evaluation datasets.

