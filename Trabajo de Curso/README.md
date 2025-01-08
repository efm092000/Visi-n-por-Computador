# Trabajo de Curso: Finger Painting


## Authors
- [Elena's GitHub](https://github.com/efm092000)
- [Ilka's GitHub](https://github.com/jeski73)

## Technologies
  - Python

## Libraries
  - OpenCV
  - Matplotlib
  - NumPy
  - ...
  - Mediapipe
  - Time

## Index

1. Project Overview
2. Features
3. Technical Implementation
4. System Requirements
5. Setup and Installation
6. Usage Guide
7. Performance Optimizations
8. Conclusion

## Project Overview <a name="overview"></a>
This project implements an interactive finger painting application using computer vision techniques. 
It allows users to draw on a virtual canvas using hand gestures captured through a webcam. 
The application combines real-time hand tracking, gesture recognition, and pose estimation to create an intuitive drawing interface.

## Features <a name="features"></a>

### Ambidextrous Accessibility
The application's ambidextrous accessibility feature makes digital art creation more inclusive through a sophisticated dominant hand calibration system. 
Using MediaPipe's hand tracking, the system identifies the user's dominant hand during startup by detecting an open palm gesture. 
This initial calibration determines whether the user is left-handed or right-handed, information that becomes crucial for all subsequent interactions with the application.

The system automatically adapts its gesture recognition and interface elements based on the detected hand dominance.
For example, the *detect_dominant_hand()* function stores the handedness information (LEFT or RIGHT) and uses it to mirror gesture interpretations, and modify tracking sensitivity to account for the natural movement patterns of each hand. 
This adaptation ensures that both left-handed and right-handed users (approximately 10-12% of the global population) can use the application with equal comfort and precision, without the ergonomic challenges often present in traditional digital art tools that primarily cater to right-handed users.

### Color Selection
The color selection system offers four chosen primary colors: Red, Green, Blue, and Yellow. 
These colors were selected to provide a fundamental palette that can be easily distinguished by the computer vision system while offering enough variety for basic artistic expression. 
The colors are accessible through an interactive menu positioned on the left side of the screen, designed for quick selection without interrupting the creative flow.

### Layers
The multi-layer canvas system forms the core of the drawing interface, providing two distinct layers labeled as BACK and FRONT.
This dual-layer approach was chosen to enable sophisticated artistic compositions by allowing users to create depth and perspective in their drawings. 
The BACK layer typically serves as the background or base layer behind the drawer, while the FRONT layer enables overlays and detailed elements in front of the person. 
The ability to switch between layers dynamically during drawing sessions provides artists with greater control over their compositions and enables easy corrections without affecting other elements of their work.

To enable this feature, a total of four layers are utilized. Layers 1 and 3 correspond to the previously mentioned BACK and FRONT layers. 
For the intermediate layer, a segmentation mask of the person’s pose is extracted and applied to the captured frame.
This body segmentation technology creates realistic overlays by separating the user from the background, allowing them to see their position relative to their artwork while maintaining clean canvas areas.

Finally, the fourth layer stores the geometries that indicate the drawing mode. 
For example, a red dot at the tip of the index finger guides the user to the drawing point, while a circle over a closed fist indicates the erasing area.

### Drawing Modes
The application implements multiple drawing modes, each designed for specific artistic needs. 

The **single-finger drawing mode**, activated by the Pointing Up gesture, provides precise control ideal for detailed work like outlining or fine details. 
This mode maintains a consistent brush size of 10 pixels for predictable results. 

The **two-finger drawing mode**, triggered by the Victory gesture, introduces dynamic brush sizing based on the distance between the index and middle fingers. 
This innovative approach allows users to naturally vary their stroke width by adjusting their finger spacing, mimicking traditional artistic tools. 
Here, thin rectangles are drawn on the canvas rotated to the corresponding hand position.
The Pointing Up and Victory gestures were selected for drawing modes as they maintain stable finger positions ideal for precise control.

The **eraser** functionality, activated by the Closed Fist gesture, calculates its size based on the hand's dimensions (from wrist to middle finger mcp), providing an easy way to make corrections at different scales.
This mirrors the natural action of erasing with a rubber eraser, making the interface more intuitive for new users.

The gesture control system was designed to be intuitive and memorable, mapping natural hand positions to common drawing actions.
Therefore, the **Open Palm gesture** serves as a universal stop command, chosen for its distinct visual signature and natural association with "stopping" actions. 

### Saving Image
The application includes several advanced features to enhance the user experience. 
The T-pose detection system provides a hands-free way to save artwork, triggered when the user extends their arms horizontally. 
This gesture was chosen for its distinctiveness and low likelihood of accidental activation. 
In order to avoid making too many pictures at once, we implemented a cooldown of 5 seconds giving the possibility to lower the arms again.


## Technical Implementation <a name="implementation"></a>

The project integrates MediaPipe technology through two essential models. The Gesture Recognizer handles hand gesture detection with high accuracy, processing live stream data to enable real-time interaction. Running the program with low hardware, some delay can occur due to the live stream mode which processes the image asynchronicly. 
The Pose Landmarker works in parallel, detecting body poses and generating segmentation masks, which are crucial for features like T-pose detection and saving drawings.
The drawing system's implementation relies on multiple numpy arrays serving as canvases. 
These arrays maintain separate BACK and FRONT layers, allowing for complex compositions. The brush size calculation system dynamically adjusts based on finger positions, providing intuitive control over stroke width. 
Real-time frame composition is achieved through OpenCV's addWeighted function, ensuring smooth visual feedback.

## System Requirements <a name="requirements"></a>
The application requires at least Python 3.10 and a functional webcam for operation. 
Users must have the *gesture_recognizer.task* and *pose_landmarker_full.task* model files in their project directory for proper functionality.

## Setup and Installation <a name="setup"></a>
Installation begins with setting up the required libraries through pip: opencv-python, mediapipe, and numpy. After installing the libraries, users need to download and place the required model files in the project directory. For Linux systems, additional configuration of environment variables may be necessary, specifically setting QT_QPA_PLATFORM to "xcb" which is already done in our code.

## Usage Guide <a name="usage"></a>
The application workflow begins with a crucial calibration phase. 
Upon launch, users are prompted to show their dominant hand to the camera. 
This step is essential as it allows the system to optimize gesture recognition for the user's primary drawing hand and ignore potential interference from the non-dominant hand. 
The calibration process uses MediaPipe's hand tracking to establish baseline measurements for the user's hand dimensions and typical gesture positions.

Drawing interaction follows a natural progression of gestures. #The Pointing Up gesture (index finger extended) activates single-finger drawing mode, where the tip of the index finger acts as a precise drawing tool. Users should maintain a consistent distance from the camera (approximately arm's length) for optimal tracking. 
The Victory gesture enables the dynamic brush size feature, where users can create varying stroke widths by adjusting the distance between their index and middle fingers – moving the fingers closer creates thinner lines, while spreading them produces broader strokes.

The menu system is designed for minimal interruption to the creative process. 
The color palette on the left edge of the screen is activated by moving the drawing hand to that area. 
Colors are arranged vertically with sufficient spacing to prevent accidental selection. 
The layer selection menu on the right edge follows the same principle, allowing users to switch between BACK and FRONT layers with a simple hand movement. 

The T-pose saving mechanism requires proper form for reliable activation. 
Users should stand facing the camera and extend both arms horizontally at shoulder height. 
The system verifies the pose by checking shoulder and wrist positions relative to each other, requiring both arms to be within 10% of horizontal alignment. 
A successful T-pose hold for one second triggers the save function, storing the artwork with a timestamp-based filename for easy organization.

## Performance Optimizations <a name="optimizations"></a>
Since our hardware is not the best we were forced to apply some performance optimizations which can be adapted in the settings part in the beginning of the code.
Therefore, the application implements several strategies to maintain smooth performance on various hardware configurations. 

Frame rate control is implemented through a configurable FPS limiter, defaulting to 10 frames per second. This rate was chosen as the optimal balance between responsive interaction and processing overhead, as testing showed that higher frame rates provided diminishing returns in terms of user experience while significantly increasing CPU usage.

The frame processing pipeline incorporates efficient memory management techniques. Instead of creating multiple copies of each frame, the system maintains a single reference frame and applies modifications through numpy's view mechanism. This approach significantly reduces memory allocation overhead and prevents memory fragmentation during extended drawing sessions. The application also implements periodic memory cleanup every 30 seconds, releasing unused resources and preventing memory leaks that could occur from accumulated temporary arrays and image processing artifacts.

Real-time image processing optimizations include selective region updating, where only the areas affected by drawing operations are reprocessed rather than the entire frame. 
The body segmentation mask is computed using thresholding operations optimized for speed, with an adjustable threshold value that can be tuned based on lighting conditions and hardware capabilities. 
The drawing operations utilize numpy's vectorized operations wherever possible, avoiding slow pixel-by-pixel operations in favor of efficient array manipulations.

The menu interaction system uses spatial partitioning to quickly determine if the user's hand is in a menu area, avoiding unnecessary collision detection calculations. 
Gesture recognition includes a simple spatial and temporal filtering system that reduces jitter in hand tracking while maintaining responsiveness. 
These optimizations work together to create a smooth, responsive drawing experience while maintaining efficient resource usage.

## Conclusion <a name="conclusion"></a>
This project demonstrates the practical application of computer vision techniques in creating an interactive drawing application. 
It showcases the integration of multiple computer vision technologies including gesture recognition, pose estimation, and real-time image processing. 
The implementation prioritizes both functionality and performance, making it suitable for educational and practical purposes.

The use of MediaPipe for gesture and pose recognition provides robust hand tracking and gesture detection, while OpenCV enables efficient image processing and real-time visualization. 
The layered approach to drawing and the intuitive gesture controls create an engaging user experience.


## Bibliography


1. [OpenCV Documentation](https://docs.opencv.org/)
2. [GeeksforGeeks - OpenCV cv2.imshow Method](https://www.geeksforgeeks.org/python-opencv-cv2-imshow-method/)
3. [GeeksforGeeks - OpenCV cv2.circle Method](https://www.geeksforgeeks.org/python-opencv-cv2-circle-method/)
4. [OpenCV Documentation - Drawing Functions](https://docs.opencv.org/4.x/da/d6e/tutorial_py_geometric_transformations.html)
5. [MediaPipe Documentation](https://developers.google.com/mediapipe)
6. [NumPy Documentation](https://numpy.org/doc/)
---