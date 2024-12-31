# Machine Learning for Material Bragg-rod Analysis (MAMBA)
Epitaxial thin film structure prediction with a U-Net


### 1. Just Running the Analysis File:

Run these two commands first:

```
ssh lxplus-gpu
source /cvmfs/sft.cern.ch/lcg/views/LCG_103cuda/x86_64-centos9-gcc11-opt/setup.sh
```
To run the training script:
```
python3 cc_v1_train_t0p1_nloss.py
```
To run the inference script, specify the input director, model directory, and output directory. For example, to run the script for two pions:

```
python3 cc_v1_infer_t0p1_nloss.py --ipath /eos/project/c/contrast/public/solar/data/20230214_two_pions/val --mpath /eos/project/c/contrast/public/solar/models/20230214_two_pions/ --opath /eos/project/c/contrast/public/solar/output/20230214_two_pions/
```

or to run it for one specific file, which has been put in the trackster_val_testData folder:
```
python3 cc_v1_infer_t0p1_nloss.py --ipath /eos/project/c/contrast/public/solar/data/20230214_two_pions/trackster_val_testData --mpath /eos/project/c/contrast/public/solar/models/20230214_two_pions/ --opath /eos/project/c/contrast/public/solar/output/20230214_two_pions/
```
