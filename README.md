# Visual-analysis-of-moving-vehicles

This project was developed as part of the Image Analysis and Computer Vision course at Politecnico di Milano. The goal is to analyze and reconstruct the road profile using a single calibrated static camera to identify and track moving vehicles, specifically focusing on the visible wheels.

## Team Members
🧑‍🤝‍🧑Thanks to [Andrea Bertogalli](https://github.com/andberto) and [Nicolò Tombini](https://github.com/tombinic)

## Project Overview
The project involves:
- **Region Proposal Network (RPN):** An object detection network trained to detect car wheels.
- **Ellipse Detection Algorithm:** Designed to detect ellipses corresponding to the visible wheels within the proposed regions.
- **3D Point Cloud Estimation:** Estimating the 3D points on the road and interpolating the local surface.

## Motivation
The advantages of this project include:
- Reducing system cost and complexity by using a single static camera.
- Enhancing accuracy in wheel localization through deep learning techniques.
- Providing valuable data for infrastructure maintenance and urban planning.

## Methods and Techniques

### Camera Calibration
The camera was calibrated using the Zhang method, which involves:
- Capturing multiple images of a planar calibration pattern.
- Detecting feature points (e.g., corners of the checkerboard) in the images.
- Computing homographies and intrinsic camera parameters.

### Data Collection
Videos of cars were recorded under various conditions:
- Cars making large and sharp curves.
- Cars on straight roads.
- Cars going uphill.

### Network Architectures

#### ResNet50
- Pre-trained on the COCO 2017 dataset.
- Fine-tuned for wheel detection using annotated images of cars.

#### YOLOv5
- Real-time detection and classification model.
- Pre-trained on a diverse set of car images covering various orientations and lighting conditions.

### Wheels Detection
An ellipse detection algorithm was designed to select the most probable ellipses corresponding to the wheels, improving upon simple bounding box detection.

### 3D Reconstruction
Two approaches were explored:
- **Deep Learning-based Depth Estimation:** Using a Dense Prediction Transformer (DPT) model to infer depth maps from single images.
- **Geometric Approach (PnP):** Recovering extrinsic parameters from correspondences between image points and world points using a 3D wheel model.

## Results
The deep learning approach provided better 3D point cloud estimation compared to the geometric approach. Qualitative analysis of the results showed satisfactory alignment with real-world conditions.

## Conclusion
The project successfully demonstrated the feasibility of using a single static camera for 3D road reconstruction and vehicle localization. Future work could explore further improvements in the geometric approach and incorporate additional car features for enhanced accuracy.

## References
1. Kaiming He, Xiangyu Zhang, Shaoqing Ren, and Jian Sun. "Deep residual learning for image recognition." Proceedings of the IEEE conference on computer vision and pattern recognition. 2016.
2. F Rashidi Fathabadi, et al. "Box-trainer assessment system with real-time multi-class detection and tracking of laparoscopic instruments, using cnn." Acta Polytechnica Hungarica, 2022.
3. Michael Shenoda. "Lighting and rotation invariant real-time vehicle wheel detector based on yolov5." arXiv preprint arXiv:2305.17785, 2023.
4. M. Fitzgibbon, et al. "Direct least-squares fitting of ellipses." 1999.
5. René Ranftl, et al. "Vision transformers for dense prediction." 2021.
6. Alexey Dosovitskiy, et al. "An image is worth 16x16 words: Transformers for image recognition at scale." 2020.
7. Vincent Lepetit, et al. "Epnp: An accurate o(n) solution to the pnp problem." 2009.
8. Yinqiang Zheng, et al. "Revisiting the pnp problem: A fast, general and optimal solution." 2013.
