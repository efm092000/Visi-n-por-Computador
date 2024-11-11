## Práctica 5. Detección y caracterización de caras

### Contenidos

[Introduction](#Introduction)
[Face Detection](#face-detection)  
[Emotion Analysing](#emotion-analysing)  
[Mistakes and Errors](#mistakes-and-errors)


### Introduction
Our idea for this task was to create a "Simon says" game. When Simon says to change the emotion on your face and you comply successfully a point is added to your score, if you fail to comply nothing happens, but if you fall for the traps a point is taken from your score.  

There is an addedd effect to our game, for each emotion an emoji that simulates it is set on your face, like a filter. 


### Face Detection
We used the Viola Jones model [*VC_P5_detectores_VK_DNN_MCTNN.ipynb*](VC_P5_detectores_VK_DNN_MCTNN.ipynb) for detecting the key points on the face, eyes, nose and mouth. Said detection helps us align the emojis over the faces


### Emotion Analysing
In order to be able to analyze the emotions on the face we used the deepface model [*VC_P5_deepface_analyze.ipynb*](VC_P5_deepface_analyze.ipynb)


### Mistakes and Errors
There are some emotions that the model doesn't actually detect, anger and disgust. They may appear for a second on the screen over the face, but it doesn't last.

There is some mixing of the emotions fear and surprise, beacuse the facil expresion for them both is rather similar to one another. 

### Gif


## Referencias

[Castrillon11] Modesto Castrillón, Oscar Déniz, Daniel Hernández, and Javier Lorenzo. A comparison of face  and facial feature detectors based on the violajones general object detection framework. Machine Vision and Applications,2011.  
[Feng21] Yuantao Feng and Shiqi Yu and Hanyang Peng and Yan-ran Li and Jianguo Zhang. Detect Faces Efficiently: A Survey and Evaluations. IEEE Transactions on Biometrics, Behavior, and Identity Science, 2021
[Kazemi14] Vahid Kazemi and Josephine Sullivan. One Millisecond Face Alignment with an Ensemble of Regression Trees. In IEEE Conference on Computer Vision and Pattern Recognition, 2014
[Lienhart02] Rainer Lienhart and Jochen Maydt. An extended set of Haar-like features for rapid object detection. ICIP 2002  
[Viola04] Paul Viola and Michael J. Jones. Robust real-time face detection. International Journal of Computer Vision, 2004  
[Zhang16] Zhang, K., Zhang, Z., Li, Z., and Qiao, Y. Joint face detection and alignment using multitask cascaded convolutional networks. IEEE Signal Processing Letters, 2016