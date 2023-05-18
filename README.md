# Human-Action-Recognition
Computer Vision  - Innopolis University - S23

## First approach 
**Detectron2 and LSTM to recognize human actions in videos.** 

Detectron2: a powerful object detection library that is capable of detecting humans in video frames. [a link](https://github.com/facebookresearch/detectron2)

LSTM: a type of recurrent neural network that is capable of processing sequences of inputs such as time-series data.

Dataset: This dataset is comprised of 12 subjects doing the following 6 actions for 5 repetitions, filmed from 4 angles, repeated 5 times each.

 * JUMPING
 * JUMPING_JACKS
 * BOXING
 * BOXING
 * WAVING_2HANDS
 * WAVING_1HAND
 * CLAPPING_HANDS

![image](https://github.com/stuarteiffert/RNN-for-Human-Activity-Recognition-using-2D-Pose-Input/blob/master/images/boxing_all_views.gif)
-------------------------------
-------------------------------
### Steps:
* Taking keypoints from the videos (20,30,60) frames.
* Preproccessing the data.(pad, normalize, split, One-hot encode the labels).
* Define the LSTM model (128 units).
* Train and evalute the model.
for this model the dataset was limited thus the accuracy was low (approx 0.2)

## Second approach 
**CNN + LSTM (ConvLSTM)** Using a CNN to extract spatial features at a given time step in the input sequence (video) and then an LSTM to identify temporal relations between frames.
A ConvLSTM cell is a variant of an LSTM network that contains convolutions operations in the network. it is an LSTM with convolution embedded in the architecture, which makes it capable of identifying spatial features of the data while keeping into account the temporal relation.






![Screenshot from 2023-05-16 19-29-25](https://github.com/Ghadeer-Issa92/Human-Action-Recognition/assets/113966581/3a9ec0ee-01eb-4525-9515-2df8f26bf9db)

For video classification, this approach captures the spatial relation in the individual frames and the temporal relation across the different frames.
As a result of this convolution structure, the ConvLSTM is capable of taking in 3-dimensional input (width, height, num_of_channels) whereas a simple LSTM only takes in 1-dimensional input.

*more info about ConvLSTM [Here](https://medium.com/neuronio/an-introduction-to-convlstm-55c9025563a7)*

**Dataset** from  **UCF101** [dataset](https://www.crcv.ucf.edu/data/UCF101.php) Using these calsses:
  * Archery
  * BaseballPitch
  * Bowling
  * BoxingPunchingBag
  * CliffDiving
  * Drumming
  * GolfSwing
  * JumpingJack
  * PlayingGuitar
  * Punch
  * WritingOnBoard
  
    
### Steps:
* **Preprocess the Dataset** Resize the frames of the videos to a fixed width and height, and normalized the data to range `[0-1]` by dividing the pixel values with `255`.
* **Split the Data into Train and Test Set.** 
* **Construct and train the model the Model** (4 ConvLstm , 50 epochs)
* **Plot Model’s Loss & Accuracy Curves**
<!-- 
 ![output](https://github.com/Ghadeer-Issa92/Human-Action-Recognition/assets/113966581/821c95e9-a87d-49ca-81e5-69d162dde2d0) ![output1](https://github.com/Ghadeer-Issa92/Human-Action-Recognition/assets/113966581/266486c0-4fda-4a20-ad4a-64d54876a372) -->
 <img src="https://github.com/Ghadeer-Issa92/Human-Action-Recognition/assets/113966581/821c95e9-a87d-49ca-81e5-69d162dde2d0" width="250" height="250">  <img src="https://github.com/Ghadeer-Issa92/Human-Action-Recognition/assets/113966581/266486c0-4fda-4a20-ad4a-64d54876a372" width="250" height="250">
 * **Saving the trained model**

--------------------
----------------------
 ## Deploy the model using FLASK
 * Main page where you can enter Youtube video URL

 ![Screenshot from 2023-05-16 22-16-47](https://github.com/Ghadeer-Issa92/Human-Action-Recognition/assets/113966581/dea1c554-190c-4d9c-8a8a-6f7795fa189b)
 * Result page
 
 ![Screenshot from 2023-05-16 22-19-49](https://github.com/Ghadeer-Issa92/Human-Action-Recognition/assets/113966581/657fd596-633a-46c5-b419-ea462cb35293)
## How to run
* Run this [colab](https://colab.research.google.com/drive/1-ADGAnWbbJDwBPAmmqOU5msGpnjDpRFg?usp=sharing) to deploy the trained model.

`if you counter  Uploader_id error  use this` [solution](https://stackoverflow.com/questions/75495800/error-unable-to-extract-uploader-id-youtube-discord-py)  `to fix it `




