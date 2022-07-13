# yolo-detect-rtsp
Stream Yolo inference results via RTSP

## "Oh, my inference mashine has no monitor... 
how can I see my inference result in real time?" this is the background story why this tiny piece of software is created while playing with Ultralytics' Yolov3 & Yolov5. I hope to use my other computers and phones to stream the results remotely

"detect-v3-rtsp.py" is then modified from "detect.py" from "https://github.com/ultralytics/yolov3" to support RTSP stream output of the inference results in near real time.

<img src="https://user-images.githubusercontent.com/79299554/178659145-48928d3f-9c67-4301-a779-39db1875d86f.jpg" height="300"> <img src="https://user-images.githubusercontent.com/79299554/178673365-3aed1d70-317e-4f36-906c-48c5ac89f439.png" height="300">
## Prerequisites
The prerequisites for this piece of software to function are the presences of 

- An working Ultralytics' Yolov3 environment (support for Yolov5 will be added soon),
- ffmpeg (https://ffmpeg.org/), and 
- rtsp-simple-server (https://github.com/aler9/rtsp-simple-server). 

Make sure you have the prerequisites in your environments. Especially should rtsp-simple-server be initiated before using "detect-v3-rtsp.py". rtsp-simple-server acts as a RTSP publisher to publish and re-broadcast. By default, port 8554 is used unless changed.


## How to use

To use "detect-v3-rtsp.py", download it (here: https://github.com/jsccjj/yolo-detect-rtsp/raw/main/detect-v3-rtsp.py) to the Yolov3's root folder.

"detect-v3-rtsp.py" inherits all the flags from "detect.py" and has an additional flag "--rtsp-out". To turn on RTSP output, add "--rtsp-out" like this:

`python detect-v3-rtsp.py --source input --rtsp-out`

The video and streaming types of input should work just fine. Compatibilities with image input and other flags are not well tested yet and require further efforts.

Once the inference is started, "detect-v3-rtsp.py" will pipe every infered frame to ffmpeg. FFmpeg then live transcodes and outputs to rtsp://<your-machine's-ip>:8554/stream

Open streaming software like VLC and stream from the url:

`rtsp://<your-machine's-ip>:8554/stream`

Have fun.

