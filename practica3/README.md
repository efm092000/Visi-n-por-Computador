## Práctica 3. Detección y reconocimiento de formas

En esta práctica el objetivo es adquirir nociones para extraer información geométrica de objetos presentes en una imagen, con el fin de caracterizarlos y posteriormente ser capaz de identificarlos de forma automática en categorías. El cuaderno de la práctica, *VC_P3.ipynb*, contiene diversos ejemplos que permiten la detección de objetos presentes en la imagen, como paso previo a su caracterización geométrica. En este sentido, se plantea el uso del umbralizado y la detección de contornos. Para el caso concreto de monedas, se considera también la utilización de la transformada de Hough para la localización de formas circulares.

Si bien no es necesario instalar paquetes adicionales para las primeras celdas del cuaderno, de cara a poder obtener la matriz de confusión, es requisito instalar en el *environment* el paquete *scikit-learn*. Con *pip* sería algo como:

```
pip install scikit-learn seaborn
```

### Authors
- [Elena's GitHub](https://github.com/efm092000)
- [Ilka's GitHub](https://github.com/jeski73)

### Technologies
  - Python

### Libraries
  - OpenCV
  - Matplotlib
  - NumPy



## Index

1. [Task 1](#task-1)  
2. [Task 2](#task-2)


### TASK 1

### TASK 2
The objective of the code is to preprocess the images to avoid problems derived from shadows in the images, convert them to grayscale and smooth them, in order to prepare the images for further analysis.

The coordinates of the sections to be kept in each image are defined, eliminating problematic areas such as shadows. Cropping is based on these row and column boundaries.

![alt text](Task2_Image1.png)

The images in shades of gray are then converted into binary (black and white) images, where pixels below a threshold value are set to one color (0 or 255) and pixels above the threshold to another.

- For the fragment image, an inverted thresholding is applied, with a threshold value of 115, which means that pixels with a value greater than 115 are set to black (0) and pixels less than or equal to 115 become white

- For the pellet image, the threshold is 100 also with an inverted thresholding.

- For the tar image, the Otsu thresholding method is used which automatically calculates the optimal threshold based on the histogram of the image, dynamically adjusting the threshold value to obtain the best separation between the objects of interest and the background, and also with inverted thresholding

![alt text](Task2_Image2.png)

Finally, contour detection and classification is performed on thresholded images of fragments, pellets and tar. Then, it creates a confusion matrix that is visualized as a heat map to evaluate the classification performance. The classification criteria are based on geometric features such as compactness, aspect ratio, and elliptical fit of contours.

![alt text](Task2_Image3.png)