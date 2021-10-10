# Machine Vision System
<br>

> Mount Google Drive
>```
>from google.colab import drive
>drive.mount('/content/gdrive’)
>```
>
> Make a new folder 
>```
>import os
>path='/content/gdrive/MyDrive/폴더명'
>os.mkdir(path)
>```

## Camera calibration 
- [code](https://github.com/aaliyahee/MachineVision/blob/main/CameraCalibration.ipynb)<br>
- [image](https://github.com/aaliyahee/MachineVision/issues/1)

Calibration (camera matrix, distortion coefficients, rotation and translation vectors)
```
ret, mtx, dist, rvecs, tvecs = cv.calibrateCamera(objpoints, imgpoints, gray.shape[::-1], None, None)
```
가로 길이 1, 세로 길이 3, 높이 5 인 직육면체를 checkerboard (0,0,0)을 기준 (In [90])
```
axis=np.float32([[0,0,0],[0,5,0],[1,5,0],[1,0,0],[0,0,-3],[0,5,-3],[1,5,-3],[1,0,-3] ])
```
가로 길이 1, 세로 길이 3, 높이 5 인 직육면체를 checkerboard (2,2,0)을 기준 (In [91])
```
axis=np.float32([[2,2,2],[2,7,2],[3,7,2],[3,2,2],[2,2,-1],[2,7,-1],[3,7,-1],[3,2,-1]])
```

## Average filtering
- [code](https://github.com/aaliyahee/MachineVision/blob/main/AverageFiltering.ipynb)
- [image](https://github.com/aaliyahee/MachineVision/issues/2)

Kernel의 크기 3x3로 수행 (In [30])
```
blur=cv.blur(img, ksize=(3,3))
```
Kernel의 크기 5x5로 수행 (In [32])
```
blur=cv.blur(img, ksize=(5,5))
```
Kernel의 크기 7x7로 수행 (In [33])
```
blur=cv.blur(img, ksize=(7,7))
```

## Image sharpening
- [code](https://github.com/aaliyahee/MachineVision/commit/74bfa7ae725849ba2efc4a5ec4584be88df17628)
- [image](https://github.com/aaliyahee/MachineVision/issues/3)

𝛼를 2로 수행 (In [20])
```
shapened_img=np.int32(img)+2*detail 
```
𝛼를 5로 수행 (In [21])
```
shapened_img=np.int32(img)+5*detail 
```
𝛼를 7로 수행 (In [22])
```
shapened_img=np.int32(img)+7*detail 
```

## Gasussian filtering
