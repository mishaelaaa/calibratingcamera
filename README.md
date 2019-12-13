# Calibrating Camera

## Why is camera calibration important?

Whenever we are using cameras in any system, say, in autonomous driving systems in the passenger cars, we need to make sure that the camera installed in that car is accurate. When I say accurate, I mean the camera should have high precision, resolution and low or no distortion.
High precision means camera should provide same output for the same input in all kinds of environmental conditions. High resolution means that the camera should be able to decipher the smallest possible change. So, the camera should be calibrated to achieve higher accuracy and low distortion which helps in achieving the higher accurate representation of the real world in the captured images.

## What libraries you need
```
    os
    glob
    sys, argparse
    pprint
    numpy
    opencv2 (cv2)
    scipy
    matplotlib
```
## Chessboard camera calibration

A classical problem in computer vision is three-dimensional (3D) reconstruction, where one seeks to infer 3D structure about a scene from two-dimensional (2D) images of it. Practical cameras are complex devices, and photogrammetry is needed to model the relationship between image sensor measurements and the 3D world. In the standard pinhole camera model, one models the relationship between world coordinates X  and image (pixel) coordinates x  via the perspective transformation : 
```
    x = K [ R  t ] X ,  x ∈ P ^ 2 ,  X ∈ P ^ 3 , 
```
where P^n is the projective space of dimension n.

In this setting, camera calibration is the process of estimating the parameters of the 3 × 4 matrix M = K [ R t ] of the perspective model. Camera calibration is an important step in the computer vision pipeline because many subsequent algorithms require knowledge of camera parameters as input. Chessboards are often used during camera calibration because they are simple to construct, and their planar grid structure defines many natural interest points in an image. The following two methods are classic calibration techniques that often employ chessboards. 