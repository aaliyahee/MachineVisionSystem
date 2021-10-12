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

### Average filtering
- [code](https://github.com/aaliyahee/MachineVision/blob/main/AverageFiltering.ipynb)
- [image](https://github.com/aaliyahee/MachineVision/issues/2)

Kernel의 크기 변경하며 수행
```
blur = cv.blur(img, ksize=( , ))
```


### Image sharpening
- [code](https://github.com/aaliyahee/MachineVision/commit/74bfa7ae725849ba2efc4a5ec4584be88df17628)
- [image](https://github.com/aaliyahee/MachineVision/issues/3)

𝛼를 변경하며 수행
```
shapened_img = np.int32(img) + 𝛼 * detail 
```

### Gasussian filtering
- [code](https://github.com/aaliyahee/MachineVision/blob/main/GaussianFilter.ipynb)
- [image](https://github.com/aaliyahee/MachineVision/issues/4)
- [getGaussianKernel](https://docs.opencv.org/4.1.2/d4/d86/group__imgproc__filter.html#gac05a120c1ae92a6060dd0db190a61afa)
- [filter2D](https://docs.opencv.org/4.1.2/d4/d86/group__imgproc__filter.html#ga27c049795ce870216ddfb366086b5a04)

kerner1d의 outer product를 계산하여 kernel2d 생성
```
kernel2d = np.outer(kernel1d, kernel1d.transpose())
```

### Salt and pepper noise & Median filtering
- [code](https://github.com/aaliyahee/MachineVision/blob/main/SaltandPepper%26Medianfilter.ipynb)
- [image](https://github.com/aaliyahee/MachineVision/issues/5)

