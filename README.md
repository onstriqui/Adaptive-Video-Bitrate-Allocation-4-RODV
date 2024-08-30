# Adaptive Video Bitrate Allocation for RODV

## By:
- [Ons Triqui](mailto:ons.triqui@gmail.com)
- [Eman Sarah Afi](mailto:emansarahafi@gmail.com)

## Overview

This project presents a framework for adaptive video bitrate allocation in teleoperated vehicles. The framework is designed to optimize the video quality while considering the available bandwidth and the importance of different camera views. The system dynamically adjusts video resolution and bitrate based on the spatiotemporal complexity of the video content and the criticality of detected objects, ensuring efficient and effective video transmission for teleoperation.

## Proposed Solution

The solution comprises two main chains:

1. **Video Processing Chain**
2. **Object Detection Chain**

![RODV Group Presentation Report Progress 1608](https://github.com/user-attachments/assets/9ce65be4-3357-420c-a40d-ec6eba9e4c0e)

### Video Processing Chain

1. **Input Video Segment:** The input video is processed in segments to enable real-time adaptation.

2. **Spatiotemporal Complexity Feature Extraction:** This step extracts features related to the spatial and temporal complexity of the video content. These features are critical for predicting the optimal resolution and quality parameters.

3. **Optimized Resolution Prediction:** Based on the extracted features and the constraints of maximum encoding/decoding time, the system predicts an optimal set of resolutions.

4. **Optimized QP Prediction:** The system predicts an optimal Quantization Parameter (QP) for each resolution to maintain video quality while reducing bitrate.

5. **JND-based Representation Elimination:** A Just Noticeable Difference (JND) model is used to eliminate redundant video representations that may not be perceptible to the human eye, reducing unnecessary data transmission.

6. **cVBR Encoder:** The constant Variable Bitrate (cVBR) encoder encodes the video using the selected resolution, QP, and bitrate to optimize video transmission.

### Object Detection Chain

1. **Sensor Data:** Sensor data from multiple cameras is fed into the object detection module.

2. **Object Detection:** The system detects objects in the video frames captured by different cameras (L1 to L6).

3. **Prioritizing and Importance Weighting:** Detected objects are prioritized based on their importance, and weights (W1 to W6) are assigned to each camera view accordingly.

4. **Acceptable Bitrates Estimation:** Using the camera reference and importance weights, the system estimates acceptable bitrates for each camera view to ensure critical information is transmitted with higher quality.

### Integration with Available Bandwidth Prediction

- The system integrates with a bandwidth prediction model to ensure that the allocated bitrates are within the available bandwidth, allowing for real-time adjustments and preventing video quality degradation or buffering.

## Components

- **Input:** Video segments and sensor data from multiple cameras.
- **Output:** Optimally encoded video stream for teleoperation, with dynamically allocated bitrates based on object importance and available bandwidth.

## Inspiration

This framework is inspired by the Quality-Aware Dynamic Resolution Adaptation Framework for Adaptive Video Streaming, which emphasizes efficient video transmission by dynamically adjusting resolution and bitrate based on content complexity and network conditions. The original paper can be accessed [here](https://doi.org/10.1145/3625468.3652172).
