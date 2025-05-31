---
layout: page
title: FSL
description: Preprocessing MRI images with FSL
img: assets/img/fsl/fsl.png
importance: 1
category: work
related_publications: true
---

All structural MRI data were preprocessed using a combination of neuroimaging tools including **FSL (version 6.0.7.7)**, **ANTs (version 2.2.0)**, and **dcm2niix (version v1.0.20240202)**. 

Prior to preprocessing, input files were converted to standardized NIFTI_GZ format using `dcm2niix` for DICOM files and `fslchfiletype` for ANALYZE format files. The preprocessing pipeline consisted of several sequential steps to ensure data quality and standardization across multiple datasets.

### Overview of the preprocessing pipeline:

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/processing.png" title="Preprocessing Flowchart" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
    Fig SI: Flowchart of the full FSL-based preprocessing pipeline.
</div>

### Step-by-step preprocessing:

1. **File Conversion & Reorientation**
   - DICOM to NIFTI using `dcm2niix`
   - ANALYZE to NIFTI using `fslchfiletype`
   - Reoriented to standard space using `fslreorient2std`

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/reorient.png" title="Reoriented Image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
    T1w image after reorientation to standard.
</div>

2. **Bias Field Correction**
   - Applied using `N4BiasFieldCorrection` from ANTs

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/bias_corrected.png" title="Bias Corrected Image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
    Image after ANTs bias field correction.
</div>

3. **Robust FOV Cropping & Brain Extraction**
   - Used `robustfov` to crop neck/lower head
   - Skull stripping with `bet2`, intensity threshold = 0.3

<div class="row">
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/robust.png" title="Cropped FOV Image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/brain.png" title="Skull-Stripped Brain" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
    Left: Cropped image using `robustfov`; Right: Skull-stripped image using BET.
</div>

4. **Registration to MNI Space**
   - Linear registration using `FLIRT`
   - DOF = 6 and 12
   - Templates: MNI152 (1mm and 2mm)

<div class="row">
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/linreg6dof1mm.png" title="6 DOF to MNI (1mm)" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/linreg_12dof_1mm.png" title="12 DOF to MNI (1mm)" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="row mt-4">
  <div class="col-sm-6">
    {% include figure.liquid path="assets/img/fsl/lin_reg6dof2mm.png" title="6 DOF to MNI (2mm)" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-6">
    {% include figure.liquid path="assets/img/fsl/linreg_12dof_2mm.png" title="12 DOF to MNI (2mm)" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
    Linear registrations to MNI152 space using FLIRT with different DOFs and resolutions.
</div>

5. **Tissue Segmentation**
   - Performed using `FAST`
   - Segmented into 3 tissue types: CSF, GM, WM

6. **White Matter Mask Creation**
   - Thresholded WM partial volume map at 0.9

<div class="row">
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/ninad_just_white_matter.png" title="WM Map (from FAST)" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-6 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/ninad_wm_mask.png" title="Binary WM Mask" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
    White matter partial volume map and the binarized WM mask after thresholding.
</div>

7. **White Stripe Intensity Normalization**
   - Binary WM mask applied to T1w image
   - Mean WM intensity computed using `fslstats`
   - T1w image normalized using `fslmaths`

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/fsl/ninad_normalised.png" title="White Stripe Normalized T1w" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
    Final normalized T1w image using white stripe normalization.
</div>

---

### Additional Notes

Other normalization techniques including **min-max normalization** and **histogram matching** were explored. However, white stripe normalization was ultimately selected due to its **biological interpretability**—the histogram peaks corresponding to CSF, WM, and GM were consistent across datasets and visually preserved tissue contrast with minimal artifacts.

---

**Hardware & Execution Environment**  
The pipeline was parallelized and executed on an HPC cluster with the following specs:  
- CPU: Intel® Xeon® Gold 6240 (2.60GHz, dual CPUs)  
- Memory: 192 GB RAM  

This allowed robust and scalable preprocessing across large neuroimaging datasets.
