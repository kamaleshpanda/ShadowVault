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
- Extract required points for game control
```python
landmarks = results.pose_landmarks.landmark
left_hand = landmarks[15]  
right_hand = landmarks[16]  
left_shoulder = landmarks[11]  
right_shoulder = landmarks[12]  
left_hip = landmarks[23]  
right_hip = landmarks[24]  
nose = landmarks[0]
```
- Now we have coordinates -
	- X (left-right (0 -> 1))
	- Y (up-down (0 -> 1))
	- Z (Depth( distance from camera))
- These coordinates are used to detect gestures
#### Step 5 - Gesture Detection
- Convert body movement → game actions
%% For games like Subway Surfers and Temple Run, the controls are simple: move right, move left, jump, and crouch. The logic behind these controls is straightforward: jumping means both hands go above the shoulders, and crouching means the head goes down. Moving left means shifting the body to the left, and moving right means shifting the body to the right. %%
##### Gesture Controls (Motion Game)  
  **Jump (Space)**  
- Both hands go above shoulders  
```python  
if left_hand.y < left_shoulder.y and right_hand.y < right_shoulder.y:  
action = "jump"  
```  
   **Roll (Down)**  
- Head goes down (you squat)  
```python  
if nose.y > left_shoulder.y:  
action = "roll"  
```  
  **Move Left**  
- Body shifts left  
```python  
body_center = (left_hip.x + right_hip.x) / 2  
if body_center < 0.4:  
action = "left"  
```  
   **Move Right**  
- Body shifts right  
```python  
if body_center > 0.6:  
action = "right"  
```
#### Step 6 - Action Mapping
- Convert actions → key presses
```python
import pyautogui
if action == "jump":
    pyautogui.press("space")
elif action == "left":
    pyautogui.press("left")
elif action == "right":
    pyautogui.press("right")
elif action == "roll":
    pyautogui.press("down")
```
#### Step 7 - Continuous Loop
- Run everything in a loop so it becomes a real time system.
```python
while True:
    capture frame
    process frame
    detect pose
    extract landmarks
    detect gesture
    press key
```

ok