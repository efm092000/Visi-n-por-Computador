# Práctica 5. Detección y caracterización de caras

## Authors
- [Elena's GitHub](https://github.com/efm092000)
- [Ilka's GitHub](https://github.com/jeski73)

## Technologies
- **Python**

## Libraries
- **MTCNN**
- **DeepFace**
- **time**
- **random**
- **NumPy**
- **OpenCV**


## Index
1. [Introduction](#introduction) 
2. [Face Detection](#face-detection)  
3. [Emotion Analysing](#emotion-analysing)  
4. [Known Issues and Limitations](#Known-Issues-and-Limitations)


## Introduction
This project is a "Simon Says" game where players respond to emotion-based instructions given by Simon. 
When Simon commands you to display a specific emotion on your face, complying correctly earns you a point. 
If you fall for a trap instruction (where Simon doesn’t say “Simon says”), a point is deducted from your score. 
If you fail to respond correctly or don’t act at all, your score remains unchanged.

An added feature of the game is emoji overlays: 
for each detected emotion, a corresponding emoji appears on the player’s face, enhancing the visual feedback like a filter.

## How It Works

### Face Detection
The program uses three different face detection models—[Haar Cascade, DNN, and MTCNN](VC_P5_detectores_VK_DNN_MCTNN.ipynb)—allowing the game to switch between these methods to ensure consistent face detection. 
Each model helps locate facial key points (such as the eyes, nose, and mouth), which allow the program to align emojis on the face accurately.
You can switch during the game by pressing *'d'*.

### Emotion Analysing
To analyze the player’s emotion, we integrated the [DeepFace library](VC_P5_deepface_analyze.ipynb), which uses pre-trained neural networks to detect emotions from facial expressions. 
This analysis enables the game to check if the player’s expression matches the current emotion command. 

### Gameplay
The game randomly selects emotions and presents them with either a "Simon says" instruction or a trap instruction. Players gain or lose points based on their responses.
Each detected emotion is displayed visually with an emoji overlay on the face, creating a nicer and interactive experience.

## Known Issues and Limitations
Some emotions, particularly anger and disgust, may not be consistently detected by the model. They might briefly appear on the screen but don’t register accurately enough for reliable gameplay.
Furthermore, the model sometimes mixes up fear and surprise due to the facial similarities between these expressions, leading to occasional misclassification.

And in general, the model’s performance can vary with lighting conditions and camera quality, affecting detection accuracy.

### Gif


## Bibliography

- [Documentation - OpenCV](https://docs.opencv.org/) 
- [Function random.choice](https://numpy.org/doc/stable/reference/random/generated/numpy.random.choice.html)
- [How to use MTCNN](https://mtcnn.readthedocs.io/en/latest/usage/)
- [Using DeepFace](https://pypi.org/project/deepface/)
- [time library](https://www.geeksforgeeks.org/python-time-module/)
