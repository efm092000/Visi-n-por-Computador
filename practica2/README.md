## Práctica 2. Funciones básicas de OpenCV

In this first assignment we have worked on image processing and for that we have used the OpenCV library in Python.

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
4. [Blue boxes](#blue-boxes)

## Canny

In this exercise we calculated the percentage of white pixels in each row and depicted the results in a chart. 
Furthermore, we calculated the rows that have the 0.95*maximum number of pixels that are white by row as well as the overall maximum of white pixels in a row. 
These are marked extra with black triangles in the chart. 

We did the same for columns. 

Lastly, we compared both results (column/row) to each other.

## Sobel

The main difference between the Sobel and the Canny, is that the Sobel is an umbralized image. 
Again, we calculated the percentage of white pixels in each row and depicted the results in a chart. 
Furthermore, we calculated the rows that have the 0.95*maximum number of pixels that are white by row as well as the overall maximum of white pixels in a row. 
These are marked extra with black triangles in the chart. 

Of course we did the same for columns again and compared the results.

The results obtained are very different, as one method inverts the black and white compared to the other. However, the results are not inverted, since the images are based on different methods (Canny - edge display - and sobel - generation of an image based on a threshold value).

## 3 frames

We decided to show 3 frames in our demonstrator to show to an external the outcome of our course. 
- The first frame is the original video.
- In the second frame we have chosen to depict a 'Andy-Warhole-Art' and changed the value of rgb.
- For the third frame we decided to demonstrate the background model subtraction.

## Blue Curtain

In this video we were inspired by the video "My little piece of privacy".
So, if someone is walking through the camera our little programm adds a blue box on top of the moving object such that it is isn't visible any more on the screen.

## Bibliografía

1. [W3Schools - Color Picker](https://www.w3schools.com/colors/colors_picker.asp)
2. [GeeksforGeeks - OpenCV cv2.imshow Method](https://www.geeksforgeeks.org/python-opencv-cv2-imshow-method/)
3. [GeeksforGeeks - OpenCV cv2.circle Method](https://www.geeksforgeeks.org/python-opencv-cv2-circle-method/)
4. [OpenCV Documentation - Drawing Functions](https://docs.opencv.org/4.x/da/d6e/tutorial_py_geometric_transformations.html)
5. [OpenCV Documentation - VideoCapture Class](https://docs.opencv.org/4.x/da/d6e/tutorial_py_geometric_transformations.html)
6. [learnopencv - OpenCV cv2.findContours Method](https://learnopencv.com/contour-detection-using-opencv-python-c/)