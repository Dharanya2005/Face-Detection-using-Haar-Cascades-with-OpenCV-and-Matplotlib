# Face-Detection-using-Haar-Cascades-with-OpenCV-and-Matplotlib
# Experiment 12
## Name : Dharanya N
## Reg no : 212223230044

## Aim

To write a Python program using OpenCV to perform the following image manipulations:  
i) Extract ROI from an image.  
ii) Perform face detection using Haar Cascades in static images.  
iii) Perform eye detection in images.  
iv) Perform face detection with label in real-time video from webcam.

## Software Required

- Anaconda - Python 3.7 or above  
- OpenCV library (`opencv-python`)  
- Matplotlib library (`matplotlib`)  
- Jupyter Notebook or any Python IDE (e.g., VS Code, PyCharm)

## Algorithm

### I) Load and Display Images

- Step 1: Import necessary packages: `numpy`, `cv2`, `matplotlib.pyplot`  
- Step 2: Load grayscale images using `cv2.imread()` with flag `0`  
- Step 3: Display images using `plt.imshow()` with `cmap='gray'`

### II) Load Haar Cascade Classifiers

- Step 1: Load face and eye cascade XML files 
### III) Perform Face Detection in Images

- Step 1: Define a function `detect_face()` that copies the input image  
- Step 2: Use `face_cascade.detectMultiScale()` to detect faces  
- Step 3: Draw white rectangles around detected faces with thickness 10  
- Step 4: Return the processed image with rectangles  

### IV) Perform Eye Detection in Images

- Step 1: Define a function `detect_eyes()` that copies the input image  
- Step 2: Use `eye_cascade.detectMultiScale()` to detect eyes  
- Step 3: Draw white rectangles around detected eyes with thickness 10  
- Step 4: Return the processed image with rectangles  

### V) Display Detection Results on Images

- Step 1: Call `detect_face()` or `detect_eyes()` on loaded images  
- Step 2: Use `plt.imshow()` with `cmap='gray'` to display images with detected regions highlighted  

### VI) Perform Face Detection on Real-Time Webcam Video

- Step 1: Capture video from webcam using `cv2.VideoCapture(0)`  
- Step 2: Loop to continuously read frames from webcam  
- Step 3: Apply `detect_face()` function on each frame  
- Step 4: Display the video frame with rectangles around detected faces  
- Step 5: Exit loop and close windows when ESC key (key code 27) is pressed  
- Step 6: Release video capture and destroy all OpenCV windows  

## Program :
```py
#Load and Display Images
import numpy as np
import cv2 
import matplotlib.pyplot as plt
%matplotlib inline
#Images
with_out_glass =cv2.imread("image_01.png",0)
with_glass = cv2.imread("image_02.png",0)
group_photo = cv2.imread("image_03.png",0)
plt.imshow(with_glass,cmap='gray')
plt.imshow(with_out_glass,cmap='gray')
plt.imshow(group_photo,cmap='gray')
#Load Haar Cascade Classifiers
# FACE DETECTION
face_cascade = cv2.CascadeClassifier("haarcascade_frontalface_default.xml")
#Perform Face Detection in Images
def detect_face(img):
    face_img = img.copy()
    face_rects = face_cascade.detectMultiScale(face_img) 
    
    for (x,y,w,h) in face_rects: 
        cv2.rectangle(face_img, (x,y), (x+w,y+h), (255,255,255), 2) 
        
    return face_img
result = detect_face(with_glass)
plt.imshow(result,cmap='gray')
result = detect_face(with_out_glass)
plt.imshow(result,cmap='gray')
# Gets errors!
result = detect_face(group_photo)
plt.imshow(result,cmap='gray')
def adj_detect_face(img):
    
    face_img = img.copy()
  
    face_rects = face_cascade.detectMultiScale(face_img,scaleFactor=1.2, minNeighbors=5) 
    
    for (x,y,w,h) in face_rects: 
        cv2.rectangle(face_img, (x,y), (x+w,y+h), (255,255,255), 2) 
        
    return face_img
# Doesn't detect the side face.
result = adj_detect_face(group_photo)
plt.imshow(result,cmap='gray')
#Perform Eye Detection in Images & Display Detection Results on Images¶
eye_cascade = cv2.CascadeClassifier("haarcascade_eye.xml")
def detect_eyes(img):
    
    face_img = img.copy()
  
    eyes = eye_cascade.detectMultiScale(face_img) 
    
    
    for (x,y,w,h) in eyes: 
        cv2.rectangle(face_img, (x,y), (x+w,y+h), (255,255,255), 2) 
        
    return face_img
result = detect_eyes(with_glass)
plt.imshow(result,cmap='gray')
eyes = eye_cascade.detectMultiScale(with_out_glass) 
# White around the pupils is not distinct enough to detect eyes here!
result = detect_eyes(group_photo)
plt.imshow(result,cmap='gray')

result = detect_eyes(with_out_glass)
plt.imshow(result,cmap='gray')

```

## Output :

### INPUT IMAGES :

<img width="440" height="418" alt="download" src="https://github.com/user-attachments/assets/05e88605-8d00-4a32-b8fb-b25a57eaf8a2" />



<img width="344" height="418" alt="download" src="https://github.com/user-attachments/assets/d7bf5d71-1234-4396-9c3b-ddac9b0f6925" />




<img width="566" height="355" alt="download" src="https://github.com/user-attachments/assets/1cf9613c-b6d4-475c-86fe-e7c1dab6ed0c" />



### FACE DETECTION :

<img width="440" height="418" alt="download" src="https://github.com/user-attachments/assets/3a5883c9-93bd-460d-b700-a8e9cdde1f35" />




<img width="344" height="418" alt="download" src="https://github.com/user-attachments/assets/ce02ff65-95e0-40f6-9f7e-2bff73f1087d" />



<img width="566" height="355" alt="download" src="https://github.com/user-attachments/assets/5b6e672c-3fbb-4dfc-ae59-210533c7be66" />
### EYE DETECTION :



<img width="440" height="418" alt="download" src="https://github.com/user-attachments/assets/c3872468-4b02-4d86-946c-c1e35765e7a1" />



<img width="566" height="355" alt="download" src="https://github.com/user-attachments/assets/a20409f5-db1c-4d06-a362-371fe9986d98" />




<img width="344" height="418" alt="download" src="https://github.com/user-attachments/assets/4f2dd330-6f7d-48b5-9eab-ab27a7b0fa60" />


## Result :

Thus, to write a Python program using OpenCV to perform image manipulations for the given objectives is executed sucessfully.
