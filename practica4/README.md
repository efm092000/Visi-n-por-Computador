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
We used 53 images to train with 50 epochs and batch size 4 because we have not that many pictures and our laptops do not have high computational power.

## Detection of People, Cars, and License Plates

Once the YOLO model was trained, we tested its ability to detect license plates, people, and cars. 
Furthermore, we also applied tracking. But since the model does not continuously detect each object correctly, it does not work in all cases.
The functionality of the model correlates to the size of the train set, which is not very big, but it detects most.

<video src="test-trackin/test-vid-track.mp4" width="320" height="240" controls>Your browser does not support the video tag.</video>

[Link to our own tracking video](test-tracking/test-vid-track.mp4)

As shown, we tested it on our own video as well as on the video provided by the instructors, which we had to upload because the file is too big for github.

## Graph
![results](https://github.com/user-attachments/assets/9fcf9735-41f6-4337-9787-c0ae543b63f4)
**Training Losses:**
- **train/box_loss:** Measures localization error in bounding boxes during training. It starts high at around 2.89 and gradually reduces, indicating model improvement in bounding box predictions.    
- **train/cls_loss:** Reflects classification loss, showing a significant drop from around 10.66 to lower values as training progresses, suggesting the model learns to classify objects more accurately over time.
- **train/dfl_loss:** This represents distribution focal loss, gradually decreasing over epochs, suggesting improved performance in distinguishing between object and background.
    
**Validation Losses:**
- **val/box_loss:** A measure of bounding box error on validation data, which fluctuates but generally decreases, indicating generalization improvements.
- **val/cls_loss:** Shows the validation classification loss, with a high start that reduces as training continues, though it remains higher than the training loss, indicating some overfitting.
- **val/dfl_loss:** Mirrors the behavior of the train/dfl_loss, with a similar decline, indicating improved object-background differentiation in validation data.

**Precision, Recall, and mAP:**
- **metrics/precision(B) and metrics/recall(B):** Precision (starting from near 0, peaking at 1) improves as false positives decrease. Recall (maxing out at ~0.36) suggests the model’s ability to identify relevant objects improves but might need further tuning.  
- **metrics/mAP50(B) and metrics/mAP50-95(B):** Mean Average Precision at different thresholds shows a gradual increase, indicating improved overall accuracy of object detections over epochs, though values remain moderate, hinting at room for further refinement.

**Learning Rates:**
- **lr/pg0, lr/pg1, lr/pg2:** These reflect learning rate schedules across different parameter groups, starting from 0.0002 and increasing throughout training, supporting stable learning progress without drastic rate fluctuations.

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

[Link to proposed test video - counting](https://studentsrwthaachende-my.sharepoint.com/:v:/g/personal/vuqxn68nwewtmhxs_students_rwth-aachen_de/EX1Qt9bH-i5AvV-LhMKpOnoB8gqUs6fOIGmqGOjKjvms1A?e=Jmz5DY&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D)


## Bibliography
[Documentation - Ultralytics] (https://docs.ultralytics.com/)
[Documentation - OpenCV] (https://docs.opencv.org/)
[Documentation - Pytesseract] (https://github.com/madmaze/pytesseract)
[Documentation - Pandas] (https://pandas.pydata.org/docs/)
