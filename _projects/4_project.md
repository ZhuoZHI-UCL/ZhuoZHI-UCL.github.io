---
layout: page
title: "HgbNet: predicting hemoglobin level/anemia degree from EHR data"
description: https://arxiv.org/abs/2401.12002 (under review) 
img: assets/img/project_image/project4/1.png
importance: 4
category: PhD period
giscus_comments: false
---
# [HgbNet: predicting hemoglobin level/anemia degree from EHR data](https://arxiv.org/abs/2401.12002) (under review)
## Abstract
Anemia is a prevalent medical condition that typically requires invasive blood tests for diagnosis and monitoring. Electronic health records (EHRs) have emerged as valuable data sources for numerous medical studies. EHR-based hemoglobin level/anemia degree prediction is non-invasive and rapid but still faces some challenges due to the fact that EHR data is typically an irregular multivariate time series containing a significant number of missing values and irregular time intervals. To address these issues, we introduce HgbNet, a machine learning-based prediction model that emulates clinicians' decision-making processes for hemoglobin level/anemia degree prediction. The model incorporates a NanDense layer with a missing indicator to handle missing values and employs attention mechanisms to account for both local irregularity and global irregularity. We evaluate the proposed method using two real-world datasets across two use cases. In our first use case, we predict hemoglobin level/anemia degree at moment T+1 by utilizing records from moments prior to T+1. In our second use case, we integrate all historical records with additional selected test results at moment T+1 to predict hemoglobin level/anemia degree at the same moment, T+1. HgbNet outperforms the best baseline results across all datasets and use cases. These findings demonstrate the feasibility of estimating hemoglobin levels and anemia degree from EHR data, positioning HgbNet as an effective non-invasive anemia diagnosis solution that could potentially enhance the quality of life for millions of affected individuals worldwide. To our knowledge, HgbNet is the first machine learning model leveraging EHR data for hemoglobin level/anemia degree prediction.
## Overview
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project4/1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">

</div>
The structure of the proposed HgbNet. At each time step $$t$$, the HgbNet input comprises four components: the original EHR data $$x_t$$, the feature-specific time interval matrix $$e_t$$, the missing indicator $$m_t$$, and the label time interval matrix $$\delta_t$$. The time embedding (TE) layer and NanDense layers process $$e_t$$ and $$x_t$$, respectively, before being input to the LSTM-M network alongside $$m_t$$ to generate the hidden representation $$h_t$$. Subsequently, $$\{h_1,h_2,...,h_T\}$$ interacts with itself, $$\{\hat{e}_1,\hat{e}_2,...,\hat{e}_T\}$$, and $$\{\delta_1,\delta_2,...,\delta_T\}$$ to compute three attention types, accounting for each record's interaction, local irregularity, and global irregularity. Finally, the fused hidden representation $$h_{\tau T}$$, derived from the three attention results, is employed for downstream tasks to predict hemoglobin level and anemia degree at time step $$T+1$$.

## Main results
Our evaluation of the proposed model contains two datasets (Mimic III and eICU), two tasks (hemoglobin level/anemia degree prediction) and two use cases (use all historical data up to time T to forecast the value at T+1, or integrate select data available at T+1 with the historical data to predict the value at T+1). The main experimental results are presented below. The baseline we compare with  are LSTM, T-LSTM, Data-GRU, ATTAIN, MIAM, HiTANet.

### use case 1
Initially, we plot the predicted hemoglobin levels against their corresponding true values, as illustrated in the image below (samples are sorted by
true value for easy observation). The evaluation matrix with corresponding standard deviation for hemoglobin level and anemia degree prediction are provided in tables.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project4/hgb_mimic.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The hemoglobin level prediction result of MIMIC III dataset.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project4/hgb_eicu.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The hemoglobin level prediction result of eICU dataset.
</div>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project4/hgb_matric.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The evaluation matrix for hemoglobin level estimation.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project4/anemia_matric.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The evaluation matrix for anemia degree estimation.
</div>

For hemoglobin level prediction, LSTM is the least effective, with the highest RMSE, MAE, and lowest R2 scores on both datasets.  This deficiency can be attributed to the LSTM model's inability to manage irregular time intervals and missing values. T-LSTM demonstrates improvement but underperforms compared to other baselines.  This outcome can be explained by T-LSTM's focus on irregular time intervals between visits while disregarding missing values.  The remaining models display further advancements, with the proposed HgbNet attaining the lowest RMSE and MAE, as well as the highest R2 scores in both datasets. The improvements   over the best metric from  other baselines in the two datasets are 5.2$$\%$$, 16.2$$\%$$, 0.6$$\%$$ and 19.5$$\%$$, 6.4$$\%$$, 1.9$$\%$$. Concerning the Data-GRU, ATTAIN, MIAM, and HiTANet methods, the latter two yield marginally better results than the former two, possibly due to their incorporation of various attention types. 

For anemia degree prediction, generally, the results align with the hemoglobin  prediction  findings. LSTM and T-LSTM display limited capabilities, while other baselines exhibit improvement, with HgbNet showcasing the best performance. It achieves the highest weighted precision and weighted F1 scores in both datasets. Specifically, the improvements over the best results from other baselines amount to 2.8$$\%$$, 1.3$$\%$$, 0.2$$\%$$, and 1.2$$\%$$.
In conclusion, all baseline models improve in handling irregular time series compared to traditional LSTM methods. Our proposed HgbNet consistently outperforms existing methods for both tasks across the two datasets, showcasing its superior performance.

We also analyze the effect of irregular time intervals on model performance. In practice, the interval between moments $$T$$ and $$T+1$$ is indeterminate (i.e., the patient's last diagnosis result could have been hours or days ago), and excessively large intervals may render predictions unreliable. We now aim to explore this issue further.

Due to space constraints, we employ R2 scores and F1 scores as evaluation metrics for two tasks, respectively. The prediction results under irregular time intervals for MIMIC III dataset are presented below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project4/interval_r2.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project4/interval_f1.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The matric of hemoglobin level and anemia degree prediction for MIMIC III dataset at different time intervals between T and T+1.
</div>

### use case 2
Due to the limited space, please check the [paper](https://arxiv.org/abs/2401.12002) for more results.