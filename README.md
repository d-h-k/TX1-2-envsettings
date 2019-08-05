# TX1-2-envsettings
TX1/2 envsettings



# 1

```
$ sudo apt-get install git cmake
Then clone the jetson-inference repo:

$ git clone https://github.com/dusty-nv/jetson-inference
$ cd jetson-inference
$ git submodule update --init
Remember to run the git submodule update --init step (or clone with the --recursive flag).

Python Development Packages
The Python functionality of this project is implemented through Python extension modules that provide bindings to the native C++ code using the Python C API. While configuring the project, the repo searches for versions of Python that have development packages installed on the system, and will then build the bindings for each version of Python that's present (e.g. Python 2.7, 3.6, and 3.7). It will also build numpy bindings for versions of numpy that are installed.

By default, Ubuntu comes with the libpython-dev and python-numpy packages pre-installed (which are for Python 2.7). Although the Python 3.6 interpreter is pre-installed by Ubuntu, the Python 3.6 development packages (libpython3-dev) and python3-numpy are not. These development packages are required for the bindings to build using the Python C API.

So if you want the project to create bindings for Python 3.6, install these packages before proceeding:

$ sudo apt-get install libpython3-dev python3-numpy
Installing these additional packages will enable the repo to build the extension bindings for Python 3.6, in addition to Python 2.7 (which is already pre-installed). Then after the build process, the jetson.inference and jetson.utils packages will be available to use within your Python environments.

Configuring with CMake
Next, create a build directory within the project and run cmake to configure the build. When cmake is run, a script is launched (CMakePreBuild.sh) that will install any required dependencies and download DNN models for you.

$ cd jetson-inference    # omit if pwd is already jetson-inference from above
$ mkdir build
$ cd build
$ cmake ../
```
# 2

git checkout -b ba9acef55947894966fcc3510d6d439546659a13

Link : 
```
commit ba9acef55947894966fcc3510d6d439546659a13 (origin/L4T-R28.2, origin/L4T-R28.1)
Author: dusty-nv <dustinf@nvidia.com>
Date:   Thu Aug 2 17:17:28 2018 +0000

    updates for TensorRT 4.0 + JetPack 3.3
```




# 3

sudo ./imagenet-camera


# 4
- fail...
```
lion@lion-desktop:~/jetson-inference/build/aarch64/bin$ sudo ./imagenet-camera
[gstreamer] initialized gstreamer, version 1.14.4.0
[gstreamer] gstCamera attempting to initialize with GST_SOURCE_NVARGUS, camera 0
[gstreamer] gstCamera pipeline string:
nvarguscamerasrc sensor-id=0 ! video/x-raw(memory:NVMM), width=(int)1280, height=(int)720, framerate=30/1, format=(string)NV12 ! nvvidconv flip-method=2 ! video/x-raw ! appsink name=mysink
[gstreamer] gstCamera successfully initialized with GST_SOURCE_NVARGUS, camera 0

imagenet-camera:  successfully initialized camera device
    width:  1280
   height:  720
    depth:  12 (bpp)


imageNet -- loading classification network model from:
         -- prototxt     networks/googlenet.prototxt
         -- model        networks/bvlc_googlenet.caffemodel
         -- class_labels networks/ilsvrc12_synset_words.txt
         -- input_blob   'data'
         -- output_blob  'prob'
         -- batch_size   1

[TRT]   TensorRT version 5.0.6
[TRT]   loading NVIDIA plugins...
[TRT]   completed loading NVIDIA plugins.
[TRT]   detected model format - caffe  (extension '.caffemodel')
[TRT]   desired precision specified for GPU: FASTEST
[TRT]   requested fasted precision for device GPU without providing valid calibrator, disabling INT8
[TRT]   native precisions detected for GPU:  FP32, FP16
[TRT]   selecting fastest native precision for GPU:  FP16
[TRT]   attempting to open engine cache file .1.1.GPU.FP16.engine
[TRT]   cache file not found, profiling network model on device GPU

error:  model file 'networks/bvlc_googlenet.caffemodel' was not found.
        if loading a built-in model, maybe it wasn't downloaded before.

        Run the Model Downloader tool again and select it for download:

           $ cd <jetson-inference>/tools
           $ ./download-models.sh

[TRT]   failed to load networks/bvlc_googlenet.caffemodel
[TRT]   imageNet -- failed to initialize.
imagenet-console:   failed to initialize imageNet
lion@lion-desktop:~/jetson-inference/build/aarch64/bin$ 

```
