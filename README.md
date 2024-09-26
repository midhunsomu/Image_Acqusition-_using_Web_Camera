
## Aim:
 
To write a python program using OpenCV to capture the image from the web camera and do the following image manipulations.
i) Write the frame as JPG 
ii) Display the video 
iii) Display the video by resizing the window
iv) Rotate and display the video

## Software Used
Anaconda - Python 3.7
## Algorithm
### Step 1:
Import OpenCV Package.
### Step 2:
Capture Video from Webcam. Use VideoCapture(0) to access the webcam and start capturing video.
### Step 3:
Use cv2.imread to read the video or image
### Step 4:
Use cv2.imshow to show the video
### Step 5:
End the program and close the output video window by pressing 'q'.
## Program:
``` Python
### Developed By:Midhun S
### Register No:212223240087

## i) Write the frame as JPG file
import cv2
videoCaptureObject = cv2.VideoCapture(0)

while True:
    ret, frame = videoCaptureObject.read()
    cv2.imshow('Video Feed', frame)
    key = cv2.waitKey(1) & 0xFF
    if key == ord('s'):
        cv2.imwrite(r"C:\Users\admin\Downloads\captured_frame.jpg", frame)
        print("Frame saved!")
    elif key == ord('q'):
        print("Exiting...")
        break
videoCaptureObject.release()
cv2.destroyAllWindows()

## ii) Display the video
import numpy as np
import cv2

cap = cv2.VideoCapture(0)
if not cap.isOpened():
    print("Error: Could not open video stream.")
    exit()

while True:
    ret, frame = cap.read()
    if not ret:
        print("Failed to grab frame")
        break
    
    cv2.imshow('video capture', frame)

    if cv2.waitKey(1) == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()

## iii) Display the video by resizing the window
import numpy as np
import cv2

cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    if not ret:
        break
    
    width = int(cap.get(3))  
    height = int(cap.get(4))  
    smaller_frame = cv2.resize(frame, (width // 2, height // 2))
    image = np.zeros((height, width, 3), np.uint8)

    image[:height // 2, :width // 2] = smaller_frame  
    image[height // 2:, :width // 2] = smaller_frame  
    image[:height // 2, width // 2:] = smaller_frame  
    image[height // 2:, width // 2:] = smaller_frame  

    cv2.imshow('Video Capture', image)

    if cv2.waitKey(1) == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()

## iv) Rotate and display the video
import numpy as np
import cv2

cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    if not ret:
        break
    
    width = int(cap.get(3)) 
    height = int(cap.get(4)) 

    smaller_frame = cv2.resize(frame, (width // 2, height // 2))

    image = np.zeros(frame.shape, np.uint8)

    image[:height // 2, :width // 2] = cv2.rotate(smaller_frame, cv2.ROTATE_180)
    image[:height // 2, width // 2:] = cv2.rotate(smaller_frame, cv2.ROTATE_180) 
    image[height // 2:, width // 2:] = smaller_frame 

    cv2.imshow('Video Capture', image)

    if cv2.waitKey(1) == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()

```
## Output

### i) Write the frame as JPG image
![image](https://github.com/user-attachments/assets/23d57ea6-97ea-47d0-b768-bfad2c9ca988)

### ii) Display the video
![image](https://github.com/user-attachments/assets/a133d6b8-d170-44ef-8c87-35685b5a2473)

### iii) Display the video by resizing the window
![image](https://github.com/user-attachments/assets/752270b1-d26e-4150-9f1e-4f110dd5f29f)

### iv) Rotate and display the video
![image](https://github.com/user-attachments/assets/56b08ee1-471a-4db3-9c6c-c128ec442ce8)

## Result:
Thus the image is accessed from webcamera and displayed using openCV.
