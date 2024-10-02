## Práctica 2. Funciones básicas de OpenCV

In the second assignment we have worked on analysing images, we constructed an demonstrater about our learning outcome so far and implemented a new interpretation of image processing.
To achieve all of this we have used the OpenCV library in Python.

## Authors
[Elena's Github](https://github.com/efm092000)


[Ilka's Github](https://github.com/jeski73)

## Tecnologies
  -  Python

## Libraries
  - OpenCV
  - Matplotlib
  - NumPy

## Index

1. [Canny](#canny)
2. [Sobel](#sobel)
3. [3 Frames ](#3-frames)
4. [Blue Curtain](#blue-curtain)

## Canny

![tarea-1-canny](tarea1.png)

In this exercise we calculated the percentage of white pixels in each row and depicted the results in a chart. 
Furthermore, we calculated the rows that have the 0.95*maximum number of pixels that are white by row as well as the overall maximum of white pixels in a row. 
These are marked extra with black triangles in the chart. 

We did the same for columns and compared both results (column/row) to each other.

We gave the charts the same y-axis such that you can compare the outcomes better as they stand right next to each other.

### results for canny

- maximum number of white pixels in a row: 56100

- rows with 95% white pixels of maxmimum number of white pixels:
12,
100

- maximum number of white pixels in a column: 47685

- columns with 95% white pixels of maxmimum number of white pixels:
92,
99,
104,
115,
119,
383

## Sobel

![tarea-2-sobel](tarea2.png)

The main difference between the Sobel and the Canny, is that the Sobel is an umbralized image. 
Again, we calculated the percentage of white pixels in each row and depicted the results in a chart. 
Furthermore, we calculated the rows that have the 0.95*maximum number of pixels that are white by row as well as the overall maximum of white pixels in a row. 
These are marked extra with black triangles in the chart. 

Of course we did the same for columns again and compared the results.

Again, we gave the charts the same y-axis such that you can compare the outcomes better as they stand right next to each other.


### results for sobel
- maximum number of white pixels in a row: 34935

- rows with 95% white pixels of maxmimum number of white pixels:
3,
20

- maximum number of white pixels in a column: 41055

- columns with 95% white pixels of maxmimum number of white pixels:
288

### Compare Sobel and Canny


![compare-sobel-canny](compareSobelCanny.png)

The results obtained show that the umbralization reduces a lot of noise but keeps the important shapes because the percentage of white pixels is lower but the curves stays mostly the same.


## 3 frames

![tarea-3-frames](tarea3.png)

We decided to show 3 frames in our demonstrator to show to an external the outcome of our course. We flipped both changed frames to underline more their difference to the original.

- The first frame is the original video.
- In the second frame we have chosen to depict a 'Andy-Warhole-Art' and changed the value of rgb.
- For the third frame we decided to demonstrate the background model subtraction.

## Blue Curtain

![tarea-4-blueCurtain](tarea4.png)

In this video we were inspired by the video "My little piece of privacy".
So, if someone is walking through the camera our little programm adds a blue box on top of the moving object such that it is isn't visible any more on the screen.
Additionally the drawn box fades over time such that you can see the movement's direction.

We used the cv2.findContours method to find boxes around moving objects, ignored small contours and joined the bigger contours to make one big box without whole in between. For the box-fading we created a second image or layer which starts with np.zeros. Each time we calculated the box, it is written onto this layer and the fade out is achieved by multiplying the opaque value of each pixel by 0.9. Then we add this layer to our frame.



## Bibliografía

1. [W3Schools - Color Picker](https://www.w3schools.com/colors/colors_picker.asp)
2. [GeeksforGeeks - OpenCV cv2.imshow Method](https://www.geeksforgeeks.org/python-opencv-cv2-imshow-method/)
3. [GeeksforGeeks - OpenCV cv2.circle Method](https://www.geeksforgeeks.org/python-opencv-cv2-circle-method/)
4. [OpenCV Documentation - Drawing Functions](https://docs.opencv.org/4.x/da/d6e/tutorial_py_geometric_transformations.html)
5. [OpenCV Documentation - VideoCapture Class](https://docs.opencv.org/4.x/da/d6e/tutorial_py_geometric_transformations.html)
6. [learnopencv - cv2.findContours Method](https://learnopencv.com/contour-detection-using-opencv-python-c/)
7. [OpenCV Documentation - cv2.addWeighted Method](https://docs.opencv.org/3.4/d2/de8/group__core__array.html#gafafb2513349db3bcff51f54ee5592a19)