---
title: Underwater 3D Reconstruction using imaging sonar and monocular camera
summary: TODO
tags:
  - Perception
date: '2023-05-01T00:00:00Z'

# # Optional external URL for project (replaces project detail page).
# external_link: 'https://drive.google.com/drive/folders/1QiKoDUbkspXU7acjHh91cRRhuZhNsnxe'

# image:
#   caption: Process Overview
#   focal_point: Smart

links:
  - name: Directed Study Reports
    url: https://drive.google.com/drive/folders/1QiKoDUbkspXU7acjHh91cRRhuZhNsnxe
# url_code: ''
# url_pdf: ''
# url_slides: ''
# url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
# slides: example
---

Underwater imaging refers to the process of capturing visual images or videos in an underwater environment. Underwater imaging is a critical task performed by marine robots for a wide range of applications including aquaculture, marine infrastructure inspection, coral reef supervision, and archaeological artifacts exploration. Improving underwater perception will advance autonomous capabilities of underwater vehicles, enabling increased complexity of their missions. Extending underwater imaging to underwater 3D reconstruction benefits with improved spatial accuracy conveying depth perception, enables quantitative analysis of underwater structures, among many others.

The key elements required for a dense 3D reconstruction are the depth, RGB images, and their corresponding camera poses. While optical cameras yield visibility and can be used to gather features such as color or texture, they are prone to be affected by attenuation, refraction, lack of illumination, light scattering, light absorption, and sunlight scintillation in shallow waters. Due to these factors, it is highly challenging to achieve dense 3D reconstruction in the underwater medium. Acoustic sensors have been used to improve the performance of visual odometry and scene reconstruction for underwater scenarios in recent years despite having lower resolutions. Acoustic sonars are more robust to the impediments faced by optical cameras but do not provide color information. Since both sensing modalities complement each other, they are fused to build an efficient underwater multimodal vision system, improving underwater imaging.

![screen render text](highlevelpo.png "High level process overview of underwater 3D reconstruction")
A recent state-of-the-art representation of 3D surfaces which leverages on the deployment of a Multi-Layer Perceptron (MLP) to fit a continuous function that implicitly represents a signal of interest is referred to as the Neural Implicit Representations. Thus, the objective of this project is to 3D reconstruct underwater objects using both monocular camera and multi-beam imaging sonar data employing state-of-the-art data-driven learning model representing the object surface as Neural Implicit functions.

My contributions to this are as follows,
- development of ROS-based sensor driver for [Ping360 scanning imaging sonar](https://bluerobotics.com/store/sonars/imaging-sonars/ping360-sonar-r1-rp/) and [Oculus multibeam imaging sonar](https://www.blueprintsubsea.com/downloads/oculus/UM-148-P01222-05.pdf) for real-world data acquisition
- development of ROS-based real-time custom visualizer for the Ping360 sonar
- time synchronization of sonar and monocular camera data
- processed sonar data into a format readable by the learning models
- formulated an optimization to derive the transformation matrix between the sonar and camera for extrinsic calibration of sensors
- reproduced and extended [Neusis](https://rpl.ri.cmu.edu/neusis/) for enhanced learning of the implicit surface by reducing noise and eliminating outliers.
- reproduced [SeaThru-NeRF](https://sea-thru-nerf.github.io/) and tested it with custom RGB dataset.

<!-- ![screen render text](featured.png "Process Overview") -->
### GPS coordinates derivation
The output of STARS were segmentation masks with detected shipwrecks. For each shipwreck site, the appropriate threshold intensity was determined from which thresholded segmentation masks were obtained. [Kornia's connected components](https://kornia.github.io/tutorials/nbs/connected_components.html) were used to determine the bounding boxes around the shipwrecks. The frequncy SSS is higher than the GPS present in the deployed AUV to gather shipwreck data at Lake Huron, Michigan. Finally, utilizing the periodic and discontinuous UTM coordinates and the pixel values from the thresholded segmentation masks with bouding boxes, the AUV's trajectory was interpolated and the GPS coordinates of the shipwrecks were derived with 10m accuracy and 30m resolution.  
![screen render text](bbx.png "Shipwreck Localization")
From this result, it can seen that the detected bounding box of ship matches the groundtruth GPS location. In the following image, a zoomed out view of the map can be seen. 
![screen render text](tbnms.png "Thunder Bay, Lake Huron, MI")

### Confidence-score ranking metric
The ranking was based on _confidence-score_ as the objective was to determine the site with artifacts of most archeaological importance. Thus, the mean of pixel intensities of the thresholded segmentation values were computed for every image across a shipwrehttps://sea-thru-nerf.github.io/ck site. The images with the highest mean are displayed in the result and the shipwrecks are displayed according to their rank. 
![screen render text](shipwreckResults.png)
The rows of the result indicate raw segmentation mask from STARS, their original intensity values, the thresholded images determining the boundary of the shipwrecks, the result of connected components and the bounding boxes. 
<!-- A detailed report can be viewed [here](https://drive.google.com/file/d/1Zjk1kY0urg-n3OiZrIOU0J4ylqPFSzRa/view?usp=sharing). -->