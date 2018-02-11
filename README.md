

# LabelImg

For Cam2 Team:

Optimized for labeling pedestrian on continuous video streams (especially for labeling jaywalkers)

11/18/2017:

-   This version will save each file's xml to next frame. 
    -   Once save xml for 00040.jpg as 00040.xml, it would save another copy as 00041.xml * So that for next frame you only need to shift each bounding box for a little bit, without repeating assigning box and id. 
    -   If 00041.xml exists, modifying 00040.xml won't change 00041.xml.
-   Object id Auto Increment 
    -   Once a pedestrian is marked with id=i 
    -   For next new bounding box it would automatically assigned with id=i+1 (when typing 'w' shortcut)

02/10/2018:

-   Replace PASCAL VOC's "difficult" label as "jaywalking" 
    -   During green traffic light period, when you observe a pedestrian cross the road curb and enter the traffic zone 
        -   tick the "jaywalking" box!

---



![img](https://camo.githubusercontent.com/eb7d2ba96e9069973a809c10b50533496483b1f8/68747470733a2f2f696d672e736869656c64732e696f2f707970692f762f6c6162656c696d672e737667) 



![img](https://camo.githubusercontent.com/3e7aad0d5c74795cc272b5e6318f34eb4af9157f/68747470733a2f2f696d672e736869656c64732e696f2f7472617669732f747a7574616c696e2f6c6162656c496d672e737667)

LabelImg is a graphical image annotation tool.

It is written in Python and uses Qt for its graphical interface.

Annotations are saved as XML files in PASCAL VOC format, the format used by [ImageNet](http://www.image-net.org/).

[![Demo Image](https://raw.githubusercontent.com/tzutalin/labelImg/master/demo/demo3.jpg)](https://raw.githubusercontent.com/tzutalin/labelImg/master/demo/demo3.jpg)

[![Demo Image](https://raw.githubusercontent.com/tzutalin/labelImg/master/demo/demo.jpg)](https://raw.githubusercontent.com/tzutalin/labelImg/master/demo/demo.jpg)

[Watch a demo video](https://youtu.be/p0nR2YsCY_U)

## Installation

### Download prebuilt binaries

-   [Windows & Linux](https://tzutalin.github.io/labelImg/)
-   macOS. Binaries for macOS are not yet available. Help would be appreciated. At present, it must be [built from source](https://github.com/yifanli8086/labelImg/blob/master/README.rst#macos).

Build from source ~~~~~~~~~~~~~~~~~

Linux/Ubuntu/Mac requires at least [Python 2.6](https://www.python.org/getit/) and has been tested with [PyQt 4.8](https://www.riverbankcomputing.com/software/pyqt/intro).

#### Ubuntu Linux

Python 2 + Qt4

```
sudo apt-get install pyqt4-dev-tools
sudo pip install lxml
make qt4py2
python labelImg.py
python labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

```

Python 3 + Qt5

```
sudo apt-get install pyqt5-dev-tools
sudo pip3 install lxml
make qt5py3
python3 labelImg.py
python3 labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

```

#### macOS

Python 2 + Qt4

```
brew install qt qt4
brew install libxml2
make qt4py2
python labelImg.py
python  labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

```

#### Windows

Download and setup [Python 2.6 or later](https://www.python.org/downloads/windows/), [PyQt4](https://www.riverbankcomputing.com/software/pyqt/download) and [install lxml](http://lxml.de/installation.html).

Open cmd and go to [labelImg](https://github.com/yifanli8086/labelImg/blob/master/README.rst#labelimg) directory

```
pyrcc4 -o resources.py resources.qrc
python labelImg.py
python labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

```

Get from PyPI ~~~~~~~~~~~~~~~~~ .. code:

```
pip install labelImg
labelImg
labelImg [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

```

I tested pip on Ubuntu 14.04 and 16.04. However, I didn't test pip on macOS and Windows

Use Docker ~~~~~~~~~~~~~~~~~ .. code:

```
docker run -it \
--user $(id -u) \
-e DISPLAY=unix$DISPLAY \
--workdir=$(pwd) \
--volume="/home/$USER:/home/$USER" \
--volume="/etc/group:/etc/group:ro" \
--volume="/etc/passwd:/etc/passwd:ro" \
--volume="/etc/shadow:/etc/shadow:ro" \
--volume="/etc/sudoers.d:/etc/sudoers.d:ro" \
-v /tmp/.X11-unix:/tmp/.X11-unix \
tzutalin/py2qt4

make qt4py2;./labelImg.py

```

You can pull the image which has all of the installed and required dependencies. [Watch a demo video](https://youtu.be/nw1GexJzbCI)

## Usage

Steps ~~~~~

1.  Build and launch using the instructions above.
2.  Click 'Change default saved annotation folder' in Menu/File
3.  Click 'Open Dir'
4.  Click 'Create RectBox'
5.  Click and release left mouse to select a region to annotate the rect box
6.  You can use right mouse to drag the rect box to copy or move it

The annotation will be saved to the folder you specify.

You can refer to the below hotkeys to speed up your workflow.

### Create pre-defined classes

You can edit the [data/predefined_classes.txt](https://github.com/tzutalin/labelImg/blob/master/data/predefined_classes.txt) to load pre-defined classes

### Hotkeys

| Ctrl + u | Load all of the images from a directory  |
| -------- | ---------------------------------------- |
| Ctrl + r | Change the default annotation target dir |
| Ctrl + s | Save                                     |
| Ctrl + d | Copy the current label and rect box      |
| Space    | Flag the current image as verified       |
| w        | Create a rect box                        |
| d        | Next image                               |
| a        | Previous image                           |
| del      | Delete the selected rect box             |
| Ctrl++   | Zoom in                                  |
| Ctrl--   | Zoom out                                 |
| ↑→↓←     | Keyboard arrows to move selected rect box |

How to contribute ~~~~~~~~~~~~~~~~~

Send a pull request

### License

[Free software: MIT license](https://github.com/tzutalin/labelImg/blob/master/LICENSE)

Citation: Tzutalin. LabelImg. Git code (2015). <https://github.com/tzutalin/labelImg>

### Related

1.  [ImageNet Utils](https://github.com/tzutalin/ImageNet_Utils) to download image, create a label text for machine learning, etc
2.  [Use Docker to run labelImg](https://hub.docker.com/r/tzutalin/py2qt4)

### 3. [Generating the PASCAL VOC TFRecord files](https://github.com/tensorflow/models/blob/4f32535fe7040bb1e429ad0e3c948a492a89482d/research/object_detection/g3doc/preparing_inputs.md#generating-the-pascal-voc-tfrecord-files)
