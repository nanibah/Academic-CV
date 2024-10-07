---
title: Underwater 3D Reconstruction using imaging sonar and monocular via Deep Learning models
summary: I set up the foundation for tackling 3D reconstruction of underwater environment by employing state-of-the-art Neural Implicit Representation models. This involved fusing monocular camera and multibeam sonar data, developing sensor drivers for real-world data acquisition, synchronizing sensor data, generating sonar poses for custom dataset, creating a ROS-based data collection visualizer, and reproducing 3D reconstruction deep learning model baselines on custom dataset.
tags:
  - Experience
date: '2024-04-01T00:00:00Z'

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
### Significance of underwater imaging in robotics
Underwater imaging refers to the process of capturing visual images or videos in an underwater environment. Underwater imaging is a critical task performed by marine robots for a wide range of applications including aquaculture, marine infrastructure inspection, coral reef supervision, and archaeological artifact exploration. Improving underwater perception will advance the autonomous capabilities of underwater vehicles, enabling increased mission complexity and precision in tasks such as inspection and exploration. 

### Evolving to underwater 3D reconstruction
Extending underwater imaging to 3D reconstruction offers several benefits. It enhances spatial accuracy and improves depth perception. Additionally, it enables quantitative analysis of underwater structures, providing a more comprehensive understanding of the subaquatic environment.

### Challenges in underwater 3D reconstruction 
<!-- The key elements required for dense 3D reconstruction are depth, RGB images, and their corresponding camera poses. While optical cameras yield visibility and capture features such as color and texture, they are prone to attenuation, refraction, light scattering, absorption, and sunlight scintillation in shallow waters. Due to these factors, achieving dense 3D reconstruction underwater is highly challenging.  -->
Dense 3D reconstruction requires three key elements: depth information, RGB images, and corresponding camera poses. However, underwater environments pose unique challenges for optical cameras. These challenges include attenuation, refraction, light scattering, and absorption. In shallow waters, sunlight scintillation further complicates imaging. These factors make achieving dense 3D reconstruction using exisiting state-of-the-art camera-based optical models for underwater highly challenging.

### Sensor fusion: A solution to underwater imaging challenges
Acoustic sensors, like sonars, have been increasingly used to complement visual odometry and scene reconstruction in underwater environments, offering robustness to the limitations of optical cameras, albeit at lower resolutions. Since acoustic sonars do not provide color information but can overcome visual distortions, the two sensing modalities—optical and sonar—are fused to build a robust, multimodal underwater vision system, enhancing underwater imaging.

### Leveraging Neural Implicit Representations for 3D reconstructions
A recent state-of-the-art method for representing 3D surfaces involves using a Multi-Layer Perceptron (MLP) to fit a continuous function that implicitly represents the signal of interest, referred to as Neural Implicit Representations. This project aims to address the challenge of underwater 3D reconstruction by utilizing both monocular camera and multi-beam sonar data within this framework. Specifically, the project employs a Neural Radiance Fields ([NeRF](https://arxiv.org/abs/2003.08934))-based deep learning models to represent the object’s surface. NeRF's ability to model continuous 3D surfaces with high accuracy makes it well-suited for handling the complexities of underwater environments, providing a promising solution for reconstructing underwater objects with enhanced precision.

<!-- A recent state-of-the-art representation of 3D surfaces which leverages on the deployment of a Multi-Layer Perceptron (MLP) to fit a continuous function that implicitly represents a signal of interest is referred to as the Neural Implicit Representations. Thus, the objective of this project is to 3D reconstruct underwater objects using both monocular camera and multi-beam imaging sonar data employing state-of-the-art data-driven learning model representing the object surface as Neural Implicit functions, in this case Neural Radiance Fields ([NeRF](https://arxiv.org/abs/2003.08934)) based learning model. -->

### Technical approach
![screen render text](detailedOverview.png "A detailed process overview of underwater 3D reconstruction involving acquiring real-world data, obtaining the poses of the camera and the sonar to pass them through a novel NeRF-based learning model to obtain the novel-view synthesis and underwater 3D reconstruction")

For this grand problem of 3D reconstructing underwater environments while fusing RCB data and multibeam sonar data, I set up the foundation during my time at the [FRoG lab](https://fieldrobotics.engin.umich.edu/home). My contributions to this are as follows,
- development of ROS-based sensor driver for [Ping360 scanning imaging sonar](https://bluerobotics.com/store/sonars/imaging-sonars/ping360-sonar-r1-rp/) and [Oculus multibeam imaging sonar](https://www.blueprintsubsea.com/downloads/oculus/UM-148-P01222-05.pdf) facilitating real-world data acquisition
- development of ROS-based real-time data collection visualizer for the Ping360 sonar, enabling real-time supervision during data collection
- time synchronization of sonar and monocular camera data levergaing their closest timestamps ensuring accurate data fusion
- development of data processing techniques to convert sonar data into a format compatible with baseline learning models, bridging the gap between raw sensor data and deep learning models
- derivation of the transformation matrix between the sonar and camera for extrinsic calibration of the sensors and sonar pose generation through formulatind and solving a non-linear optimization problem
- reproduced and tweaked [Neusis](https://rpl.ri.cmu.edu/neusis/) for faster learning of the implicit surface while reducing noise and eliminating outliers with simulated data.
- reproduction of testing [SeaThru-NeRF](https://sea-thru-nerf.github.io/) with acquired RGB dataset.

### Data acquistion
![screem render text](mhlTesting.jpeg "BlueROV underwater robot used for data acquistion")
The BlueROV robot was manually controlled using a joystick to navigate toward a coral reef-like object placed at the bottom of the towing tank in the [Marine Hydrodynamics Lab](https://mhl.engin.umich.edu/) (MHL). Once the object is clearly visible, the data recording rosbags were instantiated to captured multiple images of the object from various angles, fully rotating around it to facilitate a 3D reconstruction of the underwater object. The coral was also placed with a color checker, imitating the Panama dataset provided by the SeaThru-NeRF authors.

#### Ping360 visualizer
![screen render text](viz.png "Sonar data visualized as LaserScan and MarkerArray in real-time during data collection")


### Sonar pose generation via non-linear oprimization
Any NeRF-based architecture requires RBG information and camera poses. As we intend to utilize multi-modal data, we had to derive the sonar poses. The camera poses were derived using [COLAMP](https://colmap.github.io/), a general-purpose Structure-from-Motion and Multi-View Stereo pipeline given the RGB data. 
![screen render text](cameraPose.png "Visualization of camera poses derived using COLMAP")

A non-linear optimization problem was formulated and solved to derive the sonar poses given the sonar data, RGB data and the derived camera poses. This requires sonar data D<sup>s</sup> consisting of range and intensities (r, &theta;), 3D points x = (X<sub>c</sub>, Y<sub>c</sub>, Z<sub>c</sub>) sampled by the camera and camera poses P<sup>c</sup> as input and produces the transformation matrix from camera to sonar, T<sup>s</sup><sub>c</sub> along with a scaling factor, &alpha;. Pre-multiplying this transformation matrix with the camera poses produces sonar poses assuming that the sonar sampled the same 3D points as the camera. Thus, the formulated optimization problem is,

![screen render text](eqn.png)
where K is the camera intrinsics, D<sub>w</sub> is the 3D points sampled from the world frame, D<sub>s</sub> is the same world points sampled from the sonar frame, T<sup>c</sup><sub>w</sub> is a homogeneous transformation matrix cenverting 3D points from world frame to camera frame, P<sup>s</sup><sub>c</sub> is the projection of camera into sonar, which is given by coordinate to polar frame transformations.


### Reproduction of [SeaThru-NeRF](https://sea-thru-nerf.github.io/) on custom dataset
As a step towards testing our real-world data on exisitng models, SeaThru-NeRF was reproduced as it was developed for rendering photorealistic novel-views while accounting for the medium that strongly  influences the appearance of objects like foggy scenes or underwater data. While the resuts were not accurate, it led to potential investigations to mitigate the problem.
![screen render text](seaThruRes.png "Reproduction results of SeaThru-NeRF for Panama (provided by the author) and MHL (acquired) datasets") 

Upon observation, I suspect this might be due to the fact that backscaterring is not detected in the custom dataset. Despite choosing a coral reef with distinct features, the minimal variation between the consecutive frames of the input data seems to result in poor learning of the medium parameters. Despite training the model with different learning rate and batch size (as instructed by the authors), this was the best batch of results with training time of six hours. 

### [Neusis](https://rpl.ri.cmu.edu/neusis/)
Another baselinne chosen to be compared against was Neusis since the authors used MLPs to 3D reconstruct underwater objects using imaging sonar data. Neusis was reproduced using HoloOcean simulated dataset provided by the authors. The reproduced classes are 14° planeFull, 14° planeMissing, 14° submarine, 28° planeFull and 28° planeMissing respectively where the angle denotes the elevation aperture of the sonars they used.
![screen render text](neusis_rep.png "Comparison between the simulated groundtruth data, published results and the reproduced results of three different classes")

#### Truncated Signed Distance Function (TSDF)
The models was experimented wiwth to increase the learning rate by replacing the Signed Distance Function (SDF) with [TSDF](https://link.springer.com/content/pdf/10.1007/978-3-319-11755-3_40.pdf). SDF represents a 3D object as a continuous function in space. SDF returns the signed distance from any point in space to the surface of the object (primitive). The output value of this function is always a floating-point number that can have three different meanings depending on the context.
- Zero: the point is located precisely on the surface of the primitive being rendered.
- Negative: the point is inside the primitive and smaller values indicates deeper points.
- Positive: the point is outside the primitive and larger values mean it is farther away from the primitive.

When SDF is truncated at _±t_, large distances are not relevant for surface reconstruction and a restriction at the range of the values can be utilized to reduce memory footprint. In the codebase, _truncation_distance_ variable was introduces and hypertuned to value 0.23 units. The following formulation was designed implemented in the code base.
![screen render text](tsdf.png "Designed formula leveraging TSDF")

where _tsdf<sub>i</sub>_  is the truncated signed distance of the _i<sup>th</sup>_ pixel, _d<sub>t</sub>_ is the truncated distance and _d<sub>s</sub>_ is the signed distance. The concept is to conveniently use _d<sub>t</sub>_ and _d<sub>s</sub>_ depending on the situation.

![screen render text](neusis.png "Extension of the 14° planeFull class. TSDF has overcome noise near the rear end of the plane at earlier epochs")

Unfortunately, I had to leave the lab upon graduating before the integration of quantitative metrics into the Neusis codebase and testing this model on acquired data.

### Conclusion
During my time at the FRoG Lab, I believe I made significant contributions to establishing a foundation for tackling the underwater 3D reconstruction problem on multiple fronts and outlined a clear roadmap for the next steps in the project.