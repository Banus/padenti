# Padenti:  An OpenCL-accelerated Random Forests implementation for Computer Vision applications using local features

Padenti is an Open Source implementation of the Random Forests classifier specifically
suited for Computer Vision applications that use simple per-pixel local features (e.g.
class labeling, objects segmentation etc.). Both the training and the prediction are
accelerated on GPUs using the OpenCL framework.

The library has been developed by the
[Engineering for Health and Wellbeing group](http://www.ehw.ieiit.cnr.it/?q=computervision) at the
[Institute of Electronics, Computer and Telecommunication Engineering](http://www.ieiit.cnr.it)
of the National Research Council of Italy (CNR).

Features include:
- fast training of large datasets using OpenCL
- support for both NVIDIA and AMD GPUs
- support of arbitrary image pixel type and number of channels
- support of arbitrary per-pixel features through a custom OpenCL C function
  
"Padenti" is the word in Sardinian language (in its variant of the Mogoro village) for "Forest".

## Dependences and installation
### Dependences
- A GNU Linux system
- An OpenCL environment from either Nvidia or AMD
- A CPU with SS2 instructions support
- OpenCV 
- Boost (components random, filesystem, chrono and log)
- cmake (for compilation and installation)
- Doxygen (for documentation generation)

### Compilation and installation
```
git clone https://github.com/mUogoro/padenti.git padenti
cd padenti
mkdir build && cd build
cmake ..
make && make doc && make install
```

### Test

Download the dataset from `http://cims.nyu.edu/~tompson/NYU_Hand_Pose_Dataset.htm#download` (warning: 92 GB). Then launch:
```
python process_dataset.py DATASET_PATH OUT_PATH
```
where DATASET_PATH is the directory containing the original dataset images, while OUT_PATH is the processed dataset destination path. After the script execution ends, OUT_PATH contains two folders (train and test) where the processed images of the training set and the test set are stored.

For more information about library usage and a small tutorial please consult the [Doxygen documentation](http://muogoro.github.io/padenti).