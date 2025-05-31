---
layout: page
title: NeuroLight
description: MRI based Sex Classification Project
img: assets/img/neurolight/logo.png
importance: 1
category: work
related_publications: false
---

# NeuroLight

## MRI-based Sex Classification Project

**NeuroLight** is a comprehensive deep learning pipeline for sex classification from MRI data, built with PyTorch and designed for reproducibility and scalability. This page showcases features, project structure, and usage instructions in a visually engaging format.

---

## 🚀 Feature Showcase

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/neurolight/processing.png" title="MRI Data Pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/neurolight/cross_validation.png" title="Model Training" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/neurolight/sfcn.png" title="SFCN Model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <b>Left:</b> MRI data loading and preprocessing.<br>
    <b>Middle:</b> Deep neural network training for sex classification.<br>
    <b>Right:</b> Simple Fully Convolutional Network model.
</div>

---

## 📦 Project Structure

- **sex_classification.ipynb**  
  Beginner-friendly notebook for sex classification using PyTorch.  
  Step-by-step guide with dataset, model, and workflow.  
  See the [Medium Tutorial](https://medium.com/@daminininad/intro-to-ai-with-neuroimaging-data-a-end-to-end-tutorial-using-pytorch-f941c6ef547a) for a detailed walkthrough.

- **crossvalidation_sexclassification.py**  
  Implements K-Fold Cross Validation for robust model evaluation.  
  Run independently to assess generalization.

- **ddp_sex.py**  
  Distributed Data Parallel (DDP) script for efficient multi-GPU training.  
  Run with:  `torchrun –standalone –nproc_per_node=7 ddp_sex.py`

Requires correct folder structure and dependencies.

- **/data**  
- `dataset.py`: Dataset class for loading and preprocessing.
- `dataloader.py`: Handles batching, shuffling, and data loaders.

- **/utils**  
- `trainer.py`: Training loop, forward/backward passes, evaluation.
- `visualisation.py`: Visualizes training loss, confusion matrices, and more.

- **/models**  
Model architectures:
- SFCN (Shallow Fully Connected Network)
- ResNet

- **/configs**  
- `config.yaml`: Hyperparameters and model settings.

- **requirements.txt**  
Python dependencies. Install with:  `pip install -r requirements.txt`


---

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
      {% include figure.liquid loading="eager" path="assets/img/neurolight/cross_validation.png" title="K-Fold Cross-Validation" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  K-Fold cross-validation ensures robust and reliable model evaluation.
</div>

---

## 🛠️ How to Use

### 1. Clone the Repository
`git clone https://github.com/blackpearl006/Neurolight`
`cd Neurolight`


### 2. Install Dependencies
`pip install -r requirements.txt`


### 3. Run the Code

- **Tutorial Notebook**  
  Open `sex_classification.ipynb` in Jupyter and run the cells.

- **K-Fold Cross-Validation**  
  python3 crossvalidation_sexclassification.py

- **Distributed Training**  
  torchrun –standalone –nproc_per_node=7 ddp_sex.py

---

## 📁 Folder Overview

/data     - Dataset and data processing utilities
/utils    - Training and visualization scripts
/models   - Model definitions (SFCN, ResNet, etc.)
/configs  - Hyperparameter and model config files
---


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/neurolight/ddp.png" title="Distributed Training" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/neurolight/confusion_matrix.png" title="Confusion Matrix" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Distributed training (left) helps scale your experiments. Confusion matrices (right) provide model insight.
</div>

---

## 🎯 Conclusion

NeuroLight offers a robust, scalable, and well-documented pipeline for sex classification using MRI data and deep learning.  
From beginner tutorials to advanced distributed training, this project provides everything you need to advance your neuroimaging AI research.

---

*Ready to illuminate your research with NeuroLight? Dive into the code and let the discoveries begin!*