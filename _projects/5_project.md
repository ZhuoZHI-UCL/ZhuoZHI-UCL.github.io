---
layout: page
title: Multimodal Diagnosis for Pulmonary Embolism from EHR Data and CT Images
description: 2022 44th IEEE EMBC
img: assets/img/project_image/project5/cover.png
importance: 5
category: PhD period
giscus_comments: false
---
# [Multimodal Diagnosis for Pulmonary Embolism from EHR Data and CT Images](https://ieeexplore.ieee.org/abstract/document/9871041) (44th IEEE EMBC)
## Abstract
Pulmonary Embolism (PE) is a severe medical condition that can pose a significant risk to life. Traditional deep learning methods for PE diagnosis are based on Computed Tomography (CT) images and do not consider the patient's clinical context. To make full use of patient's clinical information, this article presents a multimodal fusion model ingesting Electronic Health Record (EHR) data and CT images for PE diagnosis. The proposed model is based on multilayer perception and convolutional neural networks. To remove the invalid information in the EHR data, the multidimensional scaling algorithm is performed for feature dimension reduction. The EHR data and CT images of 600 patients are used for experiments. The experiment results show that the proposed models outperform existing methods and the multimodal fusion model shows better performance than the single-input model.
## Overview

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project5/1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">

</div>
<div class="caption">
The structure of the proposed models.
</div>

## Main results
The results of comparing our proposed method MLP-2D CNN with baselines are shown in the following table, which highlights the superiority of the proposed method.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project5/2.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
The performance of different models.
</div>