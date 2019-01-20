# Yolo Object Detection
This is a project that uses yolo to detect objects in a video.  The project code is from [pyimagesearch.com](https://www.pyimagesearch.com/2018/11/12/yolo-object-detection-with-opencv/).


## Files
- videos folder: Where we store input videos here
- output folder: After running the code, the output videos will be here
- yolo-coco folder: The YOLOv3 object detector pre-trained (on the COCO dataset) model files. These were trained by the Darknet team.
- yolo_video.py

## How to use this code
1. Import the nexessary packages
import numpy as np
import argparse
import imutils
import time
import cv2
import os

2. Import test.mp4 video into input folder

3. Run this code in python shell
```python
python yolo_video.py --input videos/test.mp4 --output output/test_output.avi --yolo yolo-coco
```


## How this works
- Get LABELS from coco.names in yolo-coco folder
- Get random COLORS to asign to each LABELS
- Get yolov3.weights and yolov3.cfg
- Create the net from pretrained model with weights and config
- Import the input video as vs
- Read the vs to find grabbed and frame
- If we grabbed the video, continue. if not, stop here
- We find the Height and Width of video by frame.shape[:2]
- Contruct a blob from frame
- Feed the blob into the net as input
- Get layerOutputs by net.forward(ln):  ln is layer names
- Loop through the output detections, append boxes, confidences, classIDs that have confidence > 0.5
- Remove overlapping boxes by cv2.dnn.NMSBoxes 
- Draw boxes and texts with class and confidences
- Set up a writer to write frame to output folder

## My thoughts
After watching the output video, the model performs not so well. It thinks a pen as a knife, a calculator or a remote as a cellphone
![alt pic1][pic1.png]
![alt pic2][pic2.png]
![alt pic3][pic3.png]
![alt pic4][pic4.png]
![alt pic5][pic5.png]