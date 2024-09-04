---
title: Automated compound pulley system development for accurate VICON motion capture cameras calibration
summary: An automated calibration system leveraging compound pulley mechanism was designed and deployed to calibrate fifteen VICON motion capture cameras spaced across a three-story indoor flight space. 
# tags:
#   - Hardware
date: '2024-06-20T00:00:00Z'

# # Optional external URL for project (replaces project detail page).
# external_link: 'https://drive.google.com/drive/folders/1QiKoDUbkspXU7acjHh91cRRhuZhNsnxe'

# image:
#   caption: Process Overview
#   focal_point: Smart

links:
  - name: website
    url: https://websites.umich.edu/~dpanagou/labs/index.html
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

# gallery_item:
#   - album: hbr
#     image: outdoorTesting.jpeg
#     caption: Experimeting AMR outdoors and documenting battery consumption during uphill and downhill movements
#   - album: hbr
#     image: hbrTeam.jpeg
#     caption: Hachidori Robotics team :)
#   - album: hbr
#     image: visit.jpeg
#     caption: Explaining MGV operations during student-visits
#   - album: hbr
#     image: tesjasFAT.png
#     caption: MGV demo during Factory Assesment Tests
---

Fifteen VICON motion capture cameras spaced across a three-story indoor flight space required an accurate calibration system. Usually, for an accessible one-story space, a person waves around the calibration wand in irregular pattern covering the volume of the flight space as much as possible. The calibration wand consists of IR sensors uniquely spaced forming a T-shape. The motion capture cameras track these IR sensors as the wand is waved across the flight space. Once the cameras are calibrated, they are capable of returning the accurate position of the drone(s), thus aiding in drone localization and distributed control of aerospace systems.
<!-- ![screen render text](mecWheels.png "Positioning of mecanum wheels to achieve omnidirectional mobility") -->

My contributions to calibrating the three-story indoor flight space are as follows,
- **Automated Calibration System**: Proposed a low-cost and easily controllable automated calibration system leveraging compound pulley mechanism to control the motion of the calibration wand with minimal changes to the laboratory infrastructure, while accounting for the physical limitations of the flight space.
- **Design and Fabrication**: Designed motor mounts, motor-to-pulley couplers, and PCB board mounts. Selected and procured motors and embedded components for the automation system.
- **Software Development**: Developed software in embedded C and Python for controlling the wand motion and accessing the entire flight space.
- **Non-linear Optimization**: Determined the optimal location of the pulleys and estimated their locations via non-linear optimization techniques, as they were outside the field of view of the cameras.
- **Experimentation**: Conducted experiments to determine the optimal wand waving pattern, reducing the collective reprojection error of the cameras.
 
### Custom-designed parts
<!-- <script src="https://unpkg.com/@google/model-viewer/dist/model-viewer.js"></script>
<model-viewer src="path/to/your/model.glb" alt="3D model" auto-rotate camera-controls></model-viewer> -->


### Hardware
The underlying necessity of the problem was to access every nook and corner of the flight space usin the calibartion wand. The proposed low-cost, easily controllable solution was to introduce _n_ pulleys for _n_ corners of the flight space from the ceiling, so that by adjusting the length of the rope, the calibration wand could cover the entire volume of the flight space. Clamps were used on the vertical and horizontal bars closer to the ceiling to mount the stepper motors and pulleys, providing easy access for maintenance and visual supervision during testing. Eyebolts were used to direct the ropes to the corners of the flight space, with all the ropes coming together to control the wand motion.

### Embedded system
Every motor is controlled by an Arduino through a motor driver, and all the Arduinos are controlled by a master Raspberry Pi. During experimentation, the optimal pattern to wave the calibration wand was identified and fed as 3D waypoints to the Raspberry Pi. Allowing for hard-coding the starting location, the Raspberry Pi controls individual Arduinos to reach the desired waypoints.

<!-- ![screen render text](tejas.gif "360° maneuverability highlighting sideways and diagonal movements at client's shopfloor bearing 500kg payload") -->

<!-- {{< video src="tejas.mp4" controls="yes" >}}
360° maneuverability highlighting sideways and diagonal movements at client's shopfloor bearing 500kg payload -->

<!-- #### Photo Gallery
{{< gallery album="hbr" >}} -->