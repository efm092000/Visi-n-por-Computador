## Práctica 4. Reconocimiento de matrículas

### Contenidos

[Tarea](#41-aspectos-cubiertos)  
[YOLO](#42-yolo)  
[OCRs](#43-ocrs)  
[Detectando](#44-detectando-desde-muestro-codigo)  
[Entrenando YOLO](#45-entrenando-yolo)  
[Entrega](#46-entrega)

<!--[YOLOv7](#52-yolov7)  -->


## Training YOLO model

First we had to train the model to detect license plates for that, we first needed to use some pictures of vehicles and select the license plate in each picture and add those pictures, and their labels, to a dataset. 

After that we trained the model, with those pictures, so it woulf detect license plates. 

## Detection of people, cars and license plates 
Once the YOLO model was trained we decided to prove if it could detect license plates, people and cars. We also added for ir to blur the faces of the people it detected and the license plates of the cars in order to give a sense of anonymity 


<!-- Picture of our video with the blurs -->

As it can be seen, we tested it on our own video. But it was also tested it on the video given by the teachers.


<!-- Picture of the test video with the blurs -->

## Count of cars and people leaving the frame on the left and on the right 
Now we tried to count the amount of people and cara that leave the frame on the right and the amount of people and cars that leave the frame on the left. 

It doesnt really work because it counts the detection  by frames and so it count the same car and person multiple times, I tried to make it follow the movement of the detectio  troughout the video, but it only works sometimes.

<!-- picture -->

## Comparation of the different detection models


