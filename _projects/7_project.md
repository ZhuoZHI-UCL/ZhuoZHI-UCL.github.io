---
layout: page
title: "Research on Condition Acquisition and Fault Detection of Industrial Robot Reducer"
description: IEEE TIM, IEEE sensor journal
img: assets/img/project_image/project7/cover.png
importance: 7
category: Master period
giscus_comments: false
---
# Research on Condition Acquisition and Fault Detection of Industrial Robot Reducer ([IEEE TIM](https://ieeexplore.ieee.org/abstract/document/10172095), [IEEE sensor journal](https://ieeexplore.ieee.org/abstract/document/9661387))
This project is funded by National Internet development project (ZGZZ20190004) $352K
## Background
Industrial robots have the advantages of excellent precision and affordable operational costs and are widely utilized in automatic production. With the ongoing evolution of intelligent manufacturing, there has been much investment in industrial robots. However, these robots are susceptible to fault, leading to losses. As a result, both academic and industrial researchers are recently paying close attention to reliability Specifically, because of strong overall torque and large loads operating circumstances, the harmonic reducer has become a significant component that governs the accuracy and stiffness of industrial robots.

The harmonic reducer shown below is one of the known types of reducers that is commonly placed in the parts of industrial robots with small loads, for example, forearm, wrist, and hand. It consists of three basic components: wave generator, flex spline, and circular spline. As shown at the bottom of the figure, for every 360° clockwise rotation of the wave generator, the flex spline moves counterclockwise by the specific teeth amounts from its original position relative to the circular spline. By fixing the circular spline, and connecting the flex spline and wave generator to the child and parent payloads, respectively, a target deceleration and torque improvement can be achieved.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project7/1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
Composition of the harmonic reducer and its workflow.
</div>


The harmonic reducer has a more complex construction and working theory than its counterparts, which leads to a variety of failure categories and a high failure rate. To increase the reliability of industrial robots, it is crucial to identify harmonic reducer faults. However, current research works mostly focus on enhancing the harmonic reducer’s basic performance. Harmonic reducer fault detection is understudied and there are no public datasets. Therefore, realizing its fault detection is still a difficult problem.

## What we did?
1. We designed a test system for industrial robot reducer, including hardware selection, perception system, control system and analysis software, etc. We also published the open dataset of the harmonic reducer under different working conditions. The test system and different types of faults in harmonic reducers are shown below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project7/2.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>

</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project7/3.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project7/4.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
The test system for harmonic reducer.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project7/5.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Some abnormal workpieces. (a) Misalignment fault. (b) Composite fault. (c) Teeth fault. (d) Broken fault.
</div>

2. Based on two kinds of sensors: vibration sensors and acoustic emission sensors, we propose a denoising method (WRCTD algorithm) and two fault diagnosis frameworks (framework of the joint WRCTD and CNN-LSTM, framework of the joint WRCTD and OMA-VMD). The diagram of two frameworks are shown below.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project7/flow_chart_cnn_lstm.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project7/flow_chart_ama_vmd.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
The flow chart of the joint WRCTD and CNN-LSTM  and  the joint WRCTD and OMA-VMD fault detection framework for harmonic reducer.
</div>

## Publication and patent of the project
* [Fault Detection of the Harmonic Reducer Based on CNN-LSTM With a Novel Denoising Algorithm](https://ieeexplore.ieee.org/abstract/document/9661387), IEEE sensor journal.
* [Harmonic Reducer Fault Detection With Acoustic Emission](https://ieeexplore.ieee.org/abstract/document/10172095), IEEE Transactions on Instrumentation and Measurement.
* An early fault detection method for industrial robot harmonic reducer based on WLCTD and OMA-VMD. China Invention Patent. CN113878613A
* An early fault detection method for industrial robot harmonic reducer based on WLCTD and CNN-LSTM. China Invention Patent. CN113887702A.


