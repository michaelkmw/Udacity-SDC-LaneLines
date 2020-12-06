# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

This project detects lane lines on the road in pictures and videos using Canny Edge Detection and Hough Transform algorithms.
 
The code, test images, and test videos originated from [CarND LaneLines P1](https://github.com/udacity/CarND-LaneLines-P1)

Installation
---

To run this project, follow the setup guideline in [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md)

**NOTE:** If Miniconda is used, install Jupyter Notebook before creating the `carnd-term1` environment

```
conda install jupyter notebook
```

Usage
---

**NOTE:** Activate the `carnd-term1` environment before opening the notebook

```
activate carnd-term1
```

Alternatively, change the environment in the notebook through `Kernel -> Change kernel`

This project is coded using Jupyter Notebook. There are two ways to run the notebook:

1. Open Jupyter Notebook, navigate to the repository directory, and open `P1.ipynb`

2. Open Terminal/Anaconda prompt, navigate to the repository directory, enter the following command, and open `P1.ipynb`

```
jupyter notebook
```

Once the notebook is opened, the cells in the notebook can be run to detect lane lines on the roads in test images and videos.

Images and videos from _test_(type)_ folder will be processed, and the results are saved to _test_(type)_output_ .