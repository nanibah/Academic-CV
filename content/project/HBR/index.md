---
title: Software developemnt for Autonomous Mobile Robots and Mobile Guided Vehicles
summary: TODO
tags:
  - Planning
date: '2022-07-30T00:00:00Z'

# # Optional external URL for project (replaces project detail page).
# external_link: 'https://drive.google.com/drive/folders/1QiKoDUbkspXU7acjHh91cRRhuZhNsnxe'

# image:
#   caption: Process Overview
#   focal_point: Smart

links:
  - name: website
    url: https://hachidorirobotics.com/
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

Hachidori Robotics is a tech startup founded in 2020 to automate material and goods movement in industrial and warehousing environments through innovative autonomous mobile robot solutions. With about two million dollars investment in R&D, two patents in indoor positioning and navigation, and 20,000 plus hours of reliability testing, Hachidori's sales and marketing operations commenced in late 2022.

<!-- ![screen render text](highlevelpo.png "High level process overview of underwater 3D reconstruction") -->

My contributions as a R&D Robotics Engineer to the deployment of Autonomous Mobile Robots (AMRs) and Mobile Guided Vehicles(MGVs) are as follows,
- integration of Kalman Filter with IMU to account for signal dropout from Local Positioning System (LPS) for autonomous indoor navigation limiting AMR's positional drift to 1°
- production and rigorius testing of mini-satellites for deployment of LPS
- software development and testing of tele-operated mecanum-wheeled MGV achieving omnidirectional mobility for cutting windill blades of arbitrary cutting radii ranging from hundreds of millimeters to tens of meters    

### Mobile Guided Vehicle
![screen render text](TEJAS.png "MGV bearing windmill blade-cutting bandsaw untit")
The MGV was built for a custom application deviating from the core objective of this company being AMR development for warehouse automation. The MGV was equipped with an overhead bandsaw unit weighing about 500kg, to cut windill blades of arbitrary cutting radii ranging from hundreds of millimeters to tens of meters. The main objective was to maneuver in accordance with the shape of the distinct windmill blades retaining mm level accuracy. This was achieved by using an industrial standard joystick and mecanum wheels to maneuver the MGV to any arbitrary location.
![screen render text](mecWheels.png "Positioning of mecanum wheels to achieve omnidirectional mobility")

I designed the complete software to map the movements of joystick to the MGV employing these equations. I also developed a novel algorithm that enables precise control over the MGV's curved trajectories with versatile turning radii. The algorithm calculates and maps the individual wheel speeds (RPM) to the desired turning radius based on the joystick input by adjusting the ratio of the left and right wheel speeds and dynamically shifting the robot's central axis. 
![screen render text](tejas.gif "360° maneuverability highlighting sideways and diagonal movements at client's shopfloor bearing 500kg payload")

gallery_item:
  - album: <ALBUM FOLDER>
    image: <tesjastesting>.gif
    caption: Testing joystick mapping to the MGV
  - album: <ALBUM FOLDER>
    image: <outdoorTesting>.jpeg
    caption: Experimeting AMR outdoors and documenting battery consumption during uphill and downhill movements
  - album: <ALBUM FOLDER>
    image: <hbrTeam>.jpeg
    caption: Hachidori Robotics team :)
  - album: <ALBUM FOLDER>
    image: <visit>.jpeg
    caption: Explaining MGV operations during student-visits
  - album: <ALBUM FOLDER>
    image: <tesjasFAT>.gif
    caption: MGV demo during Factory Assesment Tests