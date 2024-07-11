# ML_Computer_Vision_on_Raspberry_Pi_guide
### Step-by-step guide to build and deploy a ML object detection (and later object tracking) model on a Raspberry Pi

# BACKGROUND
I've been part of a RoboCup (Rescue Line) team and among my task was the development of a software which had to identify and track some balls, so that the robot could pick them.
In this guide I'll try to explain my journey and to cover how to train a TensorFlow Lite ML model with your own dataset and then deploy it on a Raspberry Pi.

## REPOS
The guide is based on the code from the listed repositories:
- https://github.com/gpego/robot1
- https://github.com/gpego/tflite
- https://github.com/gpego/arduino-serial-com
- https://github.com/gpego/Python-serial-com
- https://github.com/gpego/newCode

They're quite messy 😅, that's why I'm trying to put all toghether in this guide.

## DISCLAIMER
I'm not by any mean an expert in this field therefore there might be some errors in the following instructions and I would like to apologize in advance. Anyway I'll write only after having had things working so following the guide you should be able to have something working. I'm not a native English speaker either so there may be some errors on that side too.
IF YOU HAVE ANY SUGGESTIONS, THINK SOMETHING IS WRONG, ECC. PLEASE LET ME KNOW.

# PLEASE NOTE THAT THIS IS STILL WORK-IN-PROGRESS!!

# SETUP
## HARDWARE
To deploy a TFLite model on a Raspberry Pi you'll need... You guessed it, a Raspberry Pi!
The project started with a Pi 4, then mid-development the Pi 5 came out. Below there's a small description about the Pis I've used:
- Pi 3B+: if you have one laying around it's technically usable to get started but don't expect it to perform real-time object detection
- Pi 4: started with that, if you already have one it's ok (I've tried the 2GB and 4GB), in real-time applications I was able to get ~10fps
- Pi 5 (👑): if you have to buy a Pi, buy this one (I've got the 8GB but the 4GB should be absolutely fine), definitely worth it. Works well in real time and it's also nicer during the development process

If you want to perform real-time object detection, you'll likely need a camera, I would recomend the Raspberry Pi Camera Module 3 (Wide if you need) for image quality and ease of use.

## SOFTWARE
Where it is technically possible to do the entire process on the Pi given that it is by all means a PC, I wouldn't recomend it beacuse it can be laggish and unpractical.

Given that Linux is the best choice for this kind of things I would either recommend to use a Linux system or if you use Windows, to install [WSL2](https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux) (Windows Subsystem for Linux 2) as I've done following [this guide](https://learn.microsoft.com/en-us/windows/wsl/install)


