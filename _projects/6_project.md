---
layout: page
title: "A performance compensation method for GPS/INS integrated navigation system based on CNN–LSTM during GPS outages"
description: Elsevier Measurement
img: assets/img/project_image/project6/cover.png
importance: 6
category: Master period
giscus_comments: false
---
# [A performance compensation method for GPS/INS integrated navigation system based on CNN–LSTM during GPS outages](https://www.sciencedirect.com/science/article/pii/S0263224121013968) (Elsevier Measurement)
## Abstract
When the global position system (GPS) signal is unavailable, the performance of the GPS/inertial navigation system (INS) integrated navigation system degrades severely. In this article, the performance of the ultra-low cost inertial measurement unit (IMU) is studied and the objective is to enhance its performance during GPS outages. To be specific, a performance compensation method is proposed, which consists of two parts. First, to deal with the large noise and drift of the micro-electro-mechanical system (MEMS)-based inertial measurement unit (IMU), a wavelet regional correlation threshold denoising algorithm is proposed. Then, to improve the performance of traditional LSTM network when dealing with navigation data with strong coupling, a convolutional neural network-long short-term memory (CNN–LSTM) model is formulated. It employs CNN to quickly extract the features of the input, and utilizes LSTM network to output pseudo-GPS signals as the compensation object. Finally, simulation experiments and real road tests are implemented to evaluate the proposed method. Comparison experiment results show that the proposed method can effectively improve the performance of the integrated navigation system during GPS outages.
## Overview

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project6/1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">

</div>
<div class="caption">
The compensation method proposed. (a) Training stage. (b) Prediction stage.
</div>
The compensation method is mainly divided into two stages, which are the training stage and the prediction stage, as shown above.

When the GPS signal is available, the system is working in the training stage, as shown in (a). $$W_f$$ and $$F_f$$ offered by IMU indicate the angular velocity and specific force denoised and they are input into SINS. The position $$P_{INS}$$ and velocity $$V_{INS}$$ obtained by SINS and position $$P_{GPS}$$ and velocity $$V_{GPS}$$ offered by GPS are input into KF to estimate the position error $$\delta P$$ and the velocity error $$\delta V.$$ These errors are utilized to correct the solution results of SINS and the output of the integrated navigation system $$P_{out}$$ and$$V_{out}$$ is obtained. At the same time, the CNN-LSTM model is trained to find the relationship between $$W_f, F_f$$ and $$P_{out}, V_{out}.$$

When the GPS signal is unavailable, the system is working in the prediction stage, as shown in Fig. 3(b). The CNN-LSTM model predicts the pseudo-signals $$P_{predicted}$$ and$$V_{predicted}$$ of GPS based on the input $$W_{j}$$
$$V_{predicted}$$ are input into the KF with $$P_{INS}$$ and $$F_f.$$ The $$P_{predicted}$$ and $$V_{predicted}$$ are input into the KF with $$P_{INS}$$ $$preu$$
used to correct the SINS and the output $$P_{owt}$$ and $$V_{out}$$ of the integrated navigation is obtained, which can be utilized for navigation during GPS outages.

## Experiment equipment and scene
The integrated navigation system consists of a MEMS-based IMU Mpu6050 (A gyroscope and an accelerometer are built in it) and a low-precision GPS receiver Neo-M8n. A high-precision GPS receiver ZED-F9P is utilized as the reference standard. The parameters of the sensors are shown below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project6/sensor_par.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
The parameters of all the sensors.
</div>

The carrier involved is a car. The installation diagram of the experimental devices is shown below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project6/scene.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
The installation diagram of the experimental devices
</div>

In the experiment, the sampling rate of IMU is 100 Hz, and the sampling rate of GPS is 10 Hz. As shown below, four GPS outage periods are added manually. The carrier motion states and the duration of four periods are shown below.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project6/verhical_tra.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
The vehicle’s trajectory in the experiment. (a) The satellite map. (b) The map transformed into the latitude and longitude coordinate system
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project6/outage.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
The setting of GPS outage periods.
</div>

## Experimental results
Take the GPS outage #1 as an example, the Position error in longitude, Position error in latitude, Velocity error in east direction and Velocity error in north direction are plotted and recorded as below.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project6/plot_1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
The experiment result of period #1. (a) Position error in longitude. (b) Position error in latitude. (c) Velocity error in east direction. (d) Velocity error in north direction.
</div>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/project_image/project6/matric_1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
The  evaluation metrics of  different methods during period #1.
</div>

The CNN–LSTM method reduces the minimum AMV and RMSE among other algorithms by more than 20% in all experiments. Therefore, this method has satisfied performance and can be applied to related research on performance compensation for integrated navigation system. Please check the [paper](https://www.sciencedirect.com/science/article/pii/S0263224121013968) for more results and details.