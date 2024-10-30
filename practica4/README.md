# Practice 4: License Plate Recognition

## Authors
- [Elena's GitHub](https://github.com/efm092000)
- [Ilka's GitHub](https://github.com/jeski73)

## Technologies
- **Python**

## Libraries
- **YOLO** from Ultralytics
- **NumPy**
- **pytesseract**
- **pandas**
- **OpenCV**
- **easyOCR**
- **labelme**

### Index

- [Training](#training-the-yolo-model)  
- [Detection Task](#detection-of-people-cars-and-license-plates)  
- [Extra - detect direction](#counting-people-and-cars-exiting-the-frame)  
- [Extra - Blurring](#blurring-for-privacy)


## Training the YOLO Model

First, we needed to train the model to detect license plates. For this, we collected images of vehicles, selected the license plates in each picture, and added those images along with their labels to a dataset. For labeling we used labelme

After that, we trained the model with these images so that it could effectively detect license plates. 

## Detection of People, Cars, and License Plates

Once the YOLO model was trained, we tested its ability to detect license plates, people, and cars. 
The functionality of the model correlates to the size of the train set, which is not very big, but it detects most.


<video src="test-vid-track.mp4" width="320" height="240" controls>Your browser does not support the video tag.</video>

<!-- Image of our video with blurs -->

As shown, we tested it on our own video as well as on the video provided by the instructors.

<!-- Image of the test video with blurs -->

## Counting People and Cars Exiting the Frame

Next, we attempted to count the number of people and cars exiting the frame on the left and right sides. However, this functionality did not perform optimally, as it counted detections by frames, resulting in multiple counts of the same car and person. I tried to make the system track the movement of the detections throughout the video, but it only worked occasionally.

<!-- Image -->

## Blurring for Privacy
We also implemented a version where the faces of people and license plates of cars are blurred if they are detected.


## Bibliography
