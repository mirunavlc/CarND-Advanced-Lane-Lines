# **Finding Lane Lines on the Road** 

### Prerequisites

For running this project having [Miniconda](https://docs.conda.io/en/latest/miniconda.html) helps. For short, Miniconda is a free and open-source distribution of the Python programming languages for scientific computing, that aims to simplify package management and deployment. Package versions are managed by the package management system conda. 

After having it, open a conda command prompt and create the proper environment for this project:

`conda env create -f environment_setup.yml `

This environment contains Python 3 and the necessary packages. Do not forget to activate it:

`conda activate carnd-term1`

The last dependency needed is [Jupyter Notebook](https://jupyter.org). This can be downloaded with conda also:

`conda install -c jupyter `

Now, from the root of the project run the Jupyter command to launch the server:

`jupyter notebook P1.ipynb`

This will launch the default browser with the notebook open. 
 
---

**Goal**

The proposed pipeline consists of the following main steps:

- Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
- Apply a distortion correction to raw images.
- Use color transforms, gradients, etc., to create a thresholded binary image.
- Apply a perspective transform to rectify binary image ("birds-eye view").
- Detect lane pixels and fit to find the lane boundary.
- Determine the curvature of the lane and vehicle position with respect to center.
- Warp the detected lane boundaries back onto the original image.
- Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.
---

### 1. Description

The tools used are color selection, region of interest selection, grayscaling, measuring distortion, finding corners, camera calibration, correcting for distortion, perspective transform, gradient threshold (Sobel Operator), color thresholding (RGB, HLS) , histogram, 1st & 2nd degree polynomials and radius curvature calculation (1st & 2nd derivative). 

Please check the P2.ipynb jupyter notebook to get the full details of the implementation and the step-by-step resulted pictures. 

![image1](https://github.com/mirunavlc/CarND-Advanced-Lane-Lines/blob/master/output_images/pipeline.JPG)

### 2. Potential shortcomings and suggestions

The provided solution generates a stable lane detection if the road has an uniform color. In the challenge_video.mp4 the road has an asphalt with stains and the algorithm detects edges on the color transition. The sanity check provided does not suffice because the road is uneven for a long series of frames. 

A better check of parallelism between the detected lane curves would be a good start to fix the problem. After that, a mean curve calculated from the last n-valid curves should be able to give a more pleasant video output.
