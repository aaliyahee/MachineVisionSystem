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
>path = '/content/gdrive/MyDrive/폴더명'
>os.mkdir(path)
>```

## Camera calibration 
- [code](https://github.com/aaliyahee/MachineVision/blob/main/CameraCalibration.ipynb)<br>
- ![image](https://github.com/aaliyahee/MachineVision/files/7300393/pattern.pdf)
- Calibration (camera matrix, distortion coefficients, rotation and translation vectors)
```
ret, mtx, dist, rvecs, tvecs = cv.calibrateCamera(objpoints, imgpoints, gray.shape[::-1], None, None)
```
- 가로 길이 1, 세로 길이 3, 높이 5 인 직육면체를 checkerboard (0,0,0)을 기준 (In [90])
```
axis = np.float32([[0,0,0], [0,5,0], [1,5,0], [1,0,0], [0,0,-3],[0,5,-3],[1,5,-3],[1,0,-3] ])
```
- 가로 길이 1, 세로 길이 3, 높이 5 인 직육면체를 checkerboard (2,2,0)을 기준 (In [91])
```
axis = np.float32([[2,2,2], [2,7,2], [3,7,2], [3,2,2], [2,2,-1],[2,7,-1],[3,7,-1],[3,2,-1]])
```

## Average filtering
## Image sharpening
## Separable filtering
