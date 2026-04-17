Camera → Pose Detection → Logic → Game Control

#### OpenCV
- Captures video from camera
- Converts BGR -> RGB
- Displays frames
#### MediaPipe
- open-source framework by Google to build real time CV applications
- has 33 body landmarks
	- Head & Face (0-10)
	- Upper Body (11-22)
	- Lower Body (23-32)
- each landmark has :-
	- x → horizontal (0 to 1) 
	- y → vertical (0 to 1)  
	- z → depth
### ==Why MediaPipe is perfect ?==
*Yolo is for object detection so it will not give accurate information for hands, joints etc.*
*MediaPipe is pre-trained, specially designed for human body tracking and perfect for motion games, gesture control etc.*

## Steps :-
#### Step 1 - Camera Input
- capture live video using OpenCV
- convert it into frames
```python
cap = cv2.VideoCapture(0)
ret, frame = cap.read()
```
#### Step 2 - Frame Processing 
- convert BGR -> RGB (MediaPipe needs RGB)
- Flip frame horizontally → so your movement feels natural (mirror control)
	- Optional: flip frame (mirror view)
- Resize frame → improves FPS (smooth gameplay)
```python
rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
# Mirror view (important for left/right control)  
frame = cv2.flip(frame, 1)  
# Resize for performance  
frame = cv2.resize(frame, (640, 480))
```
#### Step 3 - Pose Detection
- use of MediaPipe
```python
results.pose_landmarks(rgb)
```
#### Step 4 - Landmark Extraction
- Extract required body parts from 33 points
```python
landmarks = results.pose_landmarks.landmark
right_hand = landmarks[16]
left_knee  = landmarks[25]
nose       = landmarks[0]
```
- Now we have coordinates -
	- X (left-right)
	- Y ()
#### Step 2 - Frame Processing 
