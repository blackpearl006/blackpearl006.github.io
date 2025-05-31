---
layout: page
title: NeuroLight
description: MRI based Sex Classification Project
img: assets/img/neurolight.png
importance: 1
category: work
related_publications: false
---

# NeuroLight

## MRI-based Sex Classification Project

Every project has a beautiful feature showcase page.
It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.

To give your project a background in the portfolio page, just add the img tag to the front matter like so:

    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="MRI Data Pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="Model Training" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="Visualization Tools" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <b>Left:</b> MRI data loading and preprocessing.<br>
    <b>Middle:</b> Training deep neural networks on sex classification.<br>
    <b>Right:</b> Visualizing results and metrics.
</div>

## Project Structure

The project consists of the following key components:

### 1. `sex_classification.ipynb`
- Standalone tutorial notebook for sex classification using PyTorch.
- Step-by-step guide: model, dataset, and classification workflow.
- Detailed walkthrough in this [Medium Article](https://medium.com/@daminininad/intro-to-ai-with-neuroimaging-data-a-end-to-end-tutorial-using-pytorch-f941c6ef547a).

### 2. `crossvalidation_sexclassification.py`
- Implements K-Fold Cross Validation to evaluate model performance.
- Standalone script using PyTorch.
- Enhances model generalization.

### 3. `ddp_sex.py` (Distributed Data Parallel)
- Implements Distributed Data Parallel (DDP) for efficient multi-GPU training.
- Run with:
