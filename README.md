# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

### Step 1:
Load the required libraries like OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image from the file and convert it to grayscale using OpenCV.

### Step 3:
Apply different thresholding techniques:

Global thresholding (binary, binary inverse, truncate, to zero, to zero inverse).
Otsu’s thresholding.
Adaptive thresholding (mean, Gaussian).
### Step 4:
Store the results of each thresholding operation in a list for easy visualization.

### Step 5:
Display the original grayscale image and the thresholded images side by side using Matplotlib to compare results.


## Program
#### DEVELOPED BY: NITEESH M
#### REGISTER NUMBER: 212222230098


```python
# Load the necessary packages

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale

image = cv2.imread("IMAGE2.webp")
image_gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY) 

# Use Global thresholding to segment the image

ret, thresh_dipt1 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY)
ret, thresh_dipt2 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_BINARY_INV)
ret, thresh_dipt3 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO)
ret, thresh_dipt4 = cv2.threshold(image_gray, 86, 255, cv2.THRESH_TOZERO_INV)
ret, thresh_dipt5 = cv2.threshold(image_gray, 100, 255, cv2.THRESH_TRUNC)

# Use Otsu's method to segment the image

ret, thresh_dipt6 = cv2.threshold(image_gray, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

# Use Adaptive thresholding to segment the image

thresh_dipt7 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 2)
thresh_dipt8 = cv2.adaptiveThreshold(image_gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2)

# Display the results

titles = [
    "Gray Image", 
    "Threshold Image (Binary)", 
    "Threshold Image (Binary Inverse)", 
    "Threshold Image (To Zero)", 
    "Threshold Image (To Zero-Inverse)", 
    "Threshold Image (Truncate)", 
    "Otsu's Threshold", 
    "Adaptive Threshold (Mean)", 
    "Adaptive Threshold (Gaussian)"
]

images = [
    image_gray, thresh_dipt1, thresh_dipt2, thresh_dipt3, 
    thresh_dipt4, thresh_dipt5, thresh_dipt6, thresh_dipt7, thresh_dipt8
]

for i in range(9):
    plt.figure(figsize=(8, 8))
    plt.subplot(1, 2, 1)
    plt.title("Original Image")
    plt.imshow(image)
    plt.axis("off")
    plt.subplot(1, 2, 2)
    plt.title(titles[i])
    plt.imshow(cv2.cvtColor(images[i],cv2.COLOR_BGR2RGB))
    plt.axis("off")
    plt.show()
```
## Output

### Original Image
<br>

![image](https://github.com/user-attachments/assets/4d7635a7-3c01-433f-88ae-0f1282d91ef2)

<br>

### Global Thresholding
<br>

![image](https://github.com/user-attachments/assets/8008f158-1a9f-4c00-bf10-aa64fd84bd13)

![image](https://github.com/user-attachments/assets/242fe844-9282-47fe-9097-c21db1a1725d)

![image](https://github.com/user-attachments/assets/7bb87208-a3ee-4913-8e9a-39edb19379cd)

![image](https://github.com/user-attachments/assets/eba524ba-f926-412a-872b-8da1c628599b)

![image](https://github.com/user-attachments/assets/dcabe255-be7a-4fb5-bdd4-dfda55459def)


<br>

### Adaptive Thresholding
<br>

![image](https://github.com/user-attachments/assets/318d09de-6901-4095-99bf-4ef37887281e)

![image](https://github.com/user-attachments/assets/cf46e796-3cac-42ba-8b95-60d88eea9568)

<br>

### Optimum Global Thesholding using Otsu's Method
<br>

![image](https://github.com/user-attachments/assets/19f0d608-906f-4ea3-847d-63fdaeaf7b38)

<br>


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
