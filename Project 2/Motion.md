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


