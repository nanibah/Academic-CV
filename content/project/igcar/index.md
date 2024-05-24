---
title: "Real-time subassembly identification through data fusion of IMU and camera for an nuclear reactor core inspection system"
summary: Resolving orientation awareness challenges in nuclear reactor core inspections through an innovative numbering scheme and data fusion of IMU and camera.
tags:
  - Perception
date: '2021-06-01T00:00:00Z'

# # Optional external URL for project (replaces project detail page).
# external_link: https://github.com/peterstratton/Volume-DROID

# image:
#   caption: Volume-DROID
#   focal_point: Smart

links:
  - name: Publication
    url: https://www.inderscienceonline.com/doi/abs/10.1504/IJNEST.2023.132651
  - name: Slides
    url: https://umich-my.sharepoint.com/:p:/g/personal/nibah_umich_edu/EZCsTqYZsxBGjAFp5k5WuEUB5N0gOSpENNT0QiZMe_sQvA?e=h7O5dI

## Slides (optional).
  ## Associate this project with Markdown slides.
  ## Simply enter your slide deck's filename without extension.
  ## E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
  ## Otherwise, set `slides = ""`.
# slides: igcarViva #-slides
---

The Reactor Core Viewing System – Room Temperature (RCVS-RT) is a tool used for inspection of nucelar reactor core internals for structural deformities or foreign objects using vision probes consisting of a downward facing and two sideward facing cameras. A nuclear reactor core is of hexagonal lattice structure. Each hexagon tube is referred to as a sub-assembly. The inspection procedure involving extracting a sub-assembly and inserting the RCVS-RT. As the vision probes travels downwards, it is rotated to check for deformaties, thus giving rise to the lack of orientation awareness. In this project, this problem is resolved, achieving real-time orientational awareness by fusing data from IMU and the downward facing camera.

![screen render text](phaseEdgePattern.png)
The subassemblies can be observed as concentric circles of hexagons. So, every subassembly is assigned a unique pair of numbers (N, H). N indicates which concentric circle the subassembly belongs to and H which subassembly it is. After innovating this unique numbering scheme, we were able to identify patterns for subassemblies present in the hexogonal phase and the edge connecting two phases. The pattern for an adjacent phase will just be shifted by one side of the hexagon.

![screen render text](numberingAlgo.png "Numbering Algorithm")
Levergaing the observed patterns this numbering algorithm was proposed, tested with 1:1 nuclear reactor prototype and published. Given the (N, H) pair of the extracted subassembly, this algorithm displays the subassembly it is phasing in real-time with an accuracy of 1° by fusing data from the downward facing cameraand IMU connected to the onboard Raspberry Pi of the inspection system. 
