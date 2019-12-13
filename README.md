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

## Direct linear transformation

Direct linear transformation (DLT) calibration uses correspondences between world points and camera image points to estimate camera parameters. In particular, DLT calibration exploits the fact that the perspective pinhole camera model defines a set of similarity relations that can be solved via the direct linear transformation algorithm. 
To employ this approach, one requires accurate coordinates of a non-degenerate set of points in 3D space. A common way to achieve this is to construct a camera calibration rig (example below) built from three mutually perpendicular chessboards. Since the corners of each square are equidistant, it is straightforward to compute the 3D coordinates of each corner given the width of each square. The advantage of DLT calibration is its simplicity;
arbitrary cameras can be calibrated by solving a single homogeneous linear system. However, the practical use of DLT calibration is limited by the necessity of a 3D calibration rig and the fact that extremely accurate 3D coordinates are required to avoid numerical instability.

## Lines

Lines are another natural local image feature exploited in many computer vision systems. Geometrically, the set of all lines in a 2D image can be parametrized by polar coordinates ( ρ , θ ) describing the distance and angle, respectively, of their normal vectors with respect to the origin. The discrete Hough transform exploits this idea by transforming a spatial image into a matrix in ( ρ , θ ) -space whose ( i , j )-th entry counts the number of image edge points that lie on the line parametrized by ( ρ i , θ j ). As such, one can detect lines in an image by simply searching for local maxima of its discrete Hough transform.

The grid structure of a chessboard naturally defines two sets of parallel lines in an image of it. Therefore, one expects that line detection algorithms should successfully detect these lines in practice. Indeed, the following figure demonstrates Hough transform-based line detection applied to a perspective-transformed chessboard image. Clearly, the Hough transform is able to accurately detect the lines induced by the board squares. 