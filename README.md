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

The pipeline for training a new model is:

1. Generate training/test data with ```Generate_Data.ipynb```

2. Train a model and save the weights with  ```Train.ipynb```

3. Analyze the results with ```Analysis.ipynb```

```Generate_Data.ipynb``` generates 100,000 training CTRs/E-fields, with an additional 1000 for testing (since ```train_size = 100000 ```). The parameters that define the material are all defined at the top of the file. In addition one can change the percent the atoms are varied, ```v_r```, and the amount in Angstroms the c-spacing is varied, ```v_c```

```Train.ipynb``` trains the model. With the now generated training data, run this file to train the model. With 100,000 data points it took ~24 hours total to train, for both models.

```Analysis.ipynb``` contains the analysis. Make sure the parameters from ```Generate_Data.ipynb``` that define the material are the same in this file, if changed. 

For using MAMBA on experimental data, the changes are:

1. Adding a partially ocupied rough surface atop the film.
2. Changing the training grid in reciprocal space

For the rough surface, I've included two files: ```Generate_Data_rough.ipynb``` and ```Analysis_rough.ipynb``` which generate and analyze rough films respectively. The training file is the same, as it is agnostic to the nature of the film. I have not included the pre-trained weights and test data for this, so ```Analysis_rough.ipynb``` cannot be run directly from cloning this repo.

To change the training grid in reciprocal space, change the mesh grid, defined in the data generation file as ```[qx, qy, qz] = np.meshgrid(x, y, z)```. 

```qx```, `qy`, and `qz`


