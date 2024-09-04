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

Fifteen VICON motion capture cameras spaced across a three-story indoor flight space required an accurate calibration system. Usually, for an accessible one-story space, a person waves around the calibration wand in irregular pattern covering the volume of the volume of the flight space as much as possible. The calibration wand consists of IR sensors uniquely spaced forming a T-shape. The motion capture cameras track these IR sensors as the wand is waved across the flight space. Once the cameras are calibrated, they are capable of returning the exact position of the drone, thus aiding in rone localization and distributed control of aerospace systems.

My contributions to calibrating the three-story indoor flight space are as follows,
- proposing a low-cost and easily controllable automated calibration system leveraging compound pulley mechanism to control the motion of the calibration wand with minimal changes to the laboratory infrastructure / accounting for the physical limitations of the flight space
- design of motor mounts, motor-to-pulley couplers and PCB board mounts
- selection and procurement of motors and embedded components of the automation system
- software development in embedded C and python for controlling the wand motion acessing the entire flight space
- determining the location of the pulleys via non-linear optimization as they were outside the field of view of the cameras
- experimentd to determine the optimal wand waving pattern reducing the collective reprojection error of the cameras    

### Designed and 3D prints parts
need to display 3D view of the parts

### Hardware
The underlying necessity of the problem is to access every nook and corner of the flight spcae and the proposed low-cost easily controllable solution was to introduce _n_ pulley for _n_ corners of the flight space from the ceiling so that by adjecting the length of the ope, the calibration wand could cover the entire volume of the flight space. Given the infrastructure and to prevent the use of expensive equipments and personnel, clamps were used on the vertical and horizontal bars closer to the ceiling. A stepper motoe and a pulley was mounted on these clamps adjacent to each other providing easy access for maintenance and makes it easier for visula supervision during testing and definitely simplifies maintenance. Eyebolts were used to direct the ropes to the corners of the flight space. All these ropes comes together to control the wand motion. 

### Embedded system
Every motor is controlled by an arduino through a motor driver and all the arduinos are controlled by a master raspberry pi. During experiemntation, the optimal pattern to wave the calibration wand was identified and are fed in as 3D waypoints to the raspberry pi. Given the current location or starting with a fixated location everytime, allowing for hard coding the starting location, the raspberry pi controld individual arduinos to reach the desired waypoint. 

<!-- ![screen render text](tejas.gif "360° maneuverability highlighting sideways and diagonal movements at client's shopfloor bearing 500kg payload") -->

<!-- {{< video src="tejas.mp4" controls="yes" >}}
360° maneuverability highlighting sideways and diagonal movements at client's shopfloor bearing 500kg payload -->

<!-- #### Photo Gallery
{{< gallery album="hbr" >}} -->