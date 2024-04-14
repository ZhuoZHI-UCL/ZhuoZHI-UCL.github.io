---
layout: page
title: In‑Context Learning for Multimodal Learning with Missing Modalities and Data Scarcity
description: arXiv preprint arXiv:2403.09428, 2024 (under review)
img: assets/img/project_image/project3/1.png
importance: 3
category: PhD period
giscus_comments: false
---
# [In‑Context Learning for Multimodal Learning with Missing Modalities and Data Scarcity](https://arxiv.org/abs/2403.09428) (under review)
## Abstract
Multimodal machine learning with missing modalities is an increasingly relevant challenge arising in various applications such as healthcare. This paper extends the current research into missing modalities to the low-data regime, i.e., a downstream task has both missing modalities and limited sample size issues. This problem setting is particularly challenging and also practical as it is often expensive to get full-modality data and sufficient annotated training samples. We propose to use retrieval-augmented in-context learning to address these two crucial issues by unleashing the potential of a transformer's in-context learning ability. Diverging from existing methods, which primarily belong to the parametric paradigm and often require sufficient training samples, our work exploits the value of the available full-modality data, offering a novel perspective on resolving the challenge. The proposed data-dependent framework exhibits a higher degree of sample efficiency and is empirically demonstrated to enhance the classification model's performance on both full- and missing-modality data in the low-data regime across various multimodal learning tasks. When only 1% of the training data are available, our proposed method demonstrates an average improvement of 6.1% over a recent strong baseline across various datasets and missing states. Notably, our method also reduces the performance gap between full-modality and missing-modality data compared with the baseline. Code is [here](https://github.com/ZhuoZHI-UCL/ICL_multimodal).
## Overview
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project3/overall_framework.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">

</div>

The overview of the proposed method. **(a)** Assuming that each sample contains data with 2 modalities $$x_i^{m_1}$$ and $$x_i^{m_2}$$, we get the feature $$H_i = ({H_i}^{m_1},{H_i}^{m_2},cls_i)$$ of the sample by using a pre-trained multimodal transformer, note that $$x_i^{m_1}$$ or $$x_i^{m_2}$$ may be missed. **(b)** We use the $$cls$$ token to calculate the cosine similarity between the current sample and all full-modality training samples, and then retrieve the most similar $$Q$$ samples. **(c)** We input the pooled feature of the current sample  $$\tilde{H}_i$$ and neighbor samples $$\tilde{H}^{NN}_i$$ into the ICL module to predict the label $${\hat{y}}_i$$. Note that only the ICL module requires to be trained and the others are frozen. The retrieval-augmented operation is the same for both the training and inference processes. 

## Main results
The evaluated results for all datasets under various missing cases and sample sizes are shown in the following tables. $$r_{sub}$$ is the subsampling ratio for simulating data scarcity. F, $$m1$$, $$m2$$ refer to the sample with complete modalities, the sample only has $$m1$$ modality  and the sample only has $$m2$$ modality, respectively. ICL-CA and ICL-NTP are two solutions we propose. FT-A and FT-C mean fine tuning all layers/ classification layers in the transfer learning process. MAP is a recent SOTA baseline we compare with. Bold number indicates the best performance. 

With sufficient target dataset size (notably for $$r_{sub} > 0.1$$), FT-A exhibits superior performance, attributed to the update of all parameters in the target domain. MAP follows closely, achieving competitive results by updating fewer parameters. FT-C, on the other hand, performs the worst at all moments, due to the limited number of updated parameters. When the target data is limited, our proposed ICL method, particularly ICL-CA, demonstrates remarkable efficacy (especially for $$r_{sub} < 0.1$$), surpassing most baseline approaches. This trend intensifies as $$r_{sub}$$ decreases. Please check the [paper](https://arxiv.org/abs/2403.09428) for more results.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project3/0.1_1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project3/0.01-0.1.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>




