# Machine Learning for Material Bragg-rod Analysis (MAMBA)

The repository contains the files needed for doing MAMBA on a 12-layer film. Below are instructions to:
1. Just run the analysis file for the 12 layer film with the pre-trained model and data
2. The process for training a model on a new type of film (more or less layers, rough surface, etc.)


### 1. Just Running the Analysis File:

The analysis file is ```Analysis.ipynb```

The trained model weights are already included: ``` unet_12L_100k_30e_real.h5, unet_12L_100k_30e_imag.h5 ``` There are two trained models (one for the real, and one for the imaginary component of the field)

The training data is too large to include in this repository, but only the test data is needed for analysis. The ground truth fields are included in the files ``` x_test_12L_100k.npy, y_test_imag_12L_100k.npy, y_test_real_12L_100k.npy ```

The files containing the data to undo normalization for training are ``` means_imag_12L_100k.npy, std_imag_12L_100k.npy, etc. ```

The ground truth atomic positions are included in the files ``` all_cns_12L_100k.npy, all_o1s_12L_100k.npy, etc. ```

To run the analysis file, just run all the notebook cells sequentially. The fourier transform part for the test data takes about 20 minutes to run. For furture analysis if it is needed, these can just be calculated once and saved.


### 2. Training a New Model:

