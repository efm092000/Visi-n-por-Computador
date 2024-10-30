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
- [Videos](#videos)


## Training the YOLO Model

First, we needed to train the model to detect license plates. For this, we collected images of vehicles, selected the license plates in each picture, and added those images along with their labels to a dataset. For labeling we used labelme

After that, we trained the model with these images so that it could effectively detect license plates. 
Since our laptops are not very good we used the pretrained version to enhance the outcome.

## Detection of People, Cars, and License Plates

Once the YOLO model was trained, we tested its ability to detect license plates, people, and cars. 
Furthermore, we also applied tracking. But since the model does not continuously detect each object correctly, it does not work in all cases.
The functionality of the model correlates to the size of the train set, which is not very big, but it detects most.

<video src="test-trackin/test-vid-track.mp4" width="320" height="240" controls>Your browser does not support the video tag.</video>

[Link to our own tracking video](test-tracking/test-vid-track.mp4)

As shown, we tested it on our own video as well as on the video provided by the instructors, which we had to upload because the file is too big for github.


## Counting People and Cars Exiting the Frame

Next, we attempted to count the number of people and cars in a video. However, this functionality did not perform optimally, as it counted detections by frames, resulting in multiple counts of the same car and person. I tried to make the system track the movement of the detections throughout the video, but it only worked occasionally.

<video src="test-vid-count.mp4" width="320" height="240" controls>Your browser does not support the video tag.</video>

[Link to our own counting video](test-counting/test-vid-count.mp4)


## Blurring for Privacy
We also implemented a version where the faces of people and license plates of cars are blurred if they are detected.


<video src="test-vid-blurr.mp4" width="320" height="240" controls>Your browser does not support the video tag.</video>


[Link to our own blurring video](test-blurring/test-vid-blurr.mp4)

## Videos
Not to overload this readme, we have put all videos in the corresponding folder, same for the csv files.
Furthermore, the proposed test video was too big for github, here are the links to it:

[Link to proposed test video - tracking](https://studentsrwthaachende-my.sharepoint.com/:v:/g/personal/vuqxn68nwewtmhxs_students_rwth-aachen_de/EWBMBKyvReBEtcW7-fzpo6sBS0rs1Hq7P80SfDl1uQ1Tjw?e=UI79TA)

[Link to proposed test video - blurring](https://studentsrwthaachende-my.sharepoint.com/:v:/g/personal/vuqxn68nwewtmhxs_students_rwth-aachen_de/EbwdIwCV4r9PkTs-8CNZ86kBmEeb7F-kVlBEYMGgv--3oQ?e=3f7m7K)

[Link to proposed test video - counting](https://studentsrwthaachende-my.sharepoint.com/:v:/g/personal/vuqxn68nwewtmhxs_students_rwth-aachen_de/ERM_gY75duVMq7leT1ekikcB-ipt432gHTBJpvPpDfcsyg?e=Fj5ctg&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D)


## Bibliography
