# Machine Vision System
<br>

> Mount Google Drive
```
from google.colab import drive
drive.mount('/content/gdrive')
```
> Make a new folder 
```
import os
path='/content/gdrive/MyDrive/폴더명'
os.mkdir(path)
```
> Open Source Computer Vision (OpenCV)
```
import cv2 as cv
import numpy as np
from google.colab.patches import cv_imshow
```

<hr>

### Camera calibration 
- [code](https://github.com/aaliyahee/MachineVision/blob/main/CameraCalibration.ipynb)<br>
- [image](https://github.com/aaliyahee/MachineVision/issues/1)

Calibration (camera matrix, distortion coefficients, rotation and translation vectors)
```
ret, mtx, dist, rvecs, tvecs = cv.calibrateCamera(objpoints, imgpoints, gray.shape[::-1], None, None)
```
가로 길이 1, 세로 길이 3, 높이 5 인 직육면체를 checkerboard (0,0,0)을 기준 
```
axis = np.float32([[0,0,0], [0,5,0], [1,5,0], [1,0,0], [0,0,-3], [0,5,-3], [1,5,-3], [1,0,-3]])
```
가로 길이 1, 세로 길이 3, 높이 5 인 직육면체를 checkerboard (2,2,0)을 기준 
```
axis = np.float32([[2,2,2], [2,7,2], [3,7,2], [3,2,2], [2,2,-1], [2,7,-1], [3,7,-1], [3,2,-1]])
```
<hr>

### Average filter
- [code](https://github.com/aaliyahee/MachineVision/blob/main/AverageFiltering.ipynb)
- [image](https://github.com/aaliyahee/MachineVision/issues/2)

Kernel의 크기 변경하며 수행
```
blur = cv.blur(img, ksize=( , ))
```
<hr>

### Image sharpening
- [code](https://github.com/aaliyahee/MachineVision/commit/74bfa7ae725849ba2efc4a5ec4584be88df17628)
- [image](https://github.com/aaliyahee/MachineVision/issues/3)

𝛼를 변경하며 수행
```
shapened_img = np.int32(img) + 𝛼 * detail 
```
<hr>

### Gasussian filter
- [code]
- [image](https://github.com/aaliyahee/MachineVision/issues/4)
- [getGaussianKernel](https://docs.opencv.org/4.1.2/d4/d86/group__imgproc__filter.html#gac05a120c1ae92a6060dd0db190a61afa)
- [filter2D](https://docs.opencv.org/4.1.2/d4/d86/group__imgproc__filter.html#ga27c049795ce870216ddfb366086b5a04)

kerner1d의 outer product를 계산하여 kernel2d 생성
```
kernel2d = np.outer(kernel1d, kernel1d.transpose())
```
<hr>

### Salt and pepper noise & Median filtering
- [code](https://github.com/aaliyahee/MachineVision/blob/main/SaltandPepper%26Medianfilter.ipynb)
- [image](https://github.com/aaliyahee/MachineVision/issues/5)
 
<hr>
 
### Sobel filter
- [code](https://github.com/aaliyahee/MachineVision/blob/main/SobelFilter_gradient.ipynb)
- [image]()

<hr>

### RANSAC line fitting
- A simple but Clever Idea
  - _What we really want_: model explains many points "well"
  - _Least Squares_: model makes as few big mistakes as possible over the entire dataset
  - _New objective_: find model for which error is "small" for as many data points as possible
  - _Method_: RANSAC (**RA**ndom **SA**mple **C**onsensus)

- RANSAC: Pros and Cons <br>

  ||Pros|Cons|
  |------|---|---|
  |1|Ridiculously simple|Have to tune parameters|
  |2|Ridiculously effective|No theory (so can not derive parameters via theory)|
  |3|Works in general|Not magic, especially with lots of outliers|
  
- [code]
- [image]
- [draw line (cv.line)](https://opencv-python.readthedocs.io/en/latest/doc/03.drawShape/drawShape.html)
 
