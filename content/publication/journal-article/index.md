---
title: "Volume-DROID: A Real-Time Implementation of Volumetric Mapping with DROID-SLAM"
authors:
- admin
- Peter Stratton 
- Sandilya Sai Garimella 
- Ashwin Saxena
- Emaad Gerami
# author_notes:
# - "Equal contribution"
# - "Equal contribution"
date: "2023-04-30T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2023-07-27T00:00:00Z"

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ["article-journal"]

# Publication name and optional abbreviated publication name.
publication: "*Advances in Artificial Intelligence and Machine Learning"
publication_short: "AAIML"

abstract: This paper presents Volume-DROID, a novel approach for Simultaneous Localization and Mapping (SLAM) that integrates Volumetric Mapping and Differentiable Recurrent Optimization-Inspired Design (DROID). Volume-DROID takes camera images (monocular or stereo) or frames from a video as input and combines DROID-SLAM, point cloud registration, an off-the-shelf semantic segmentation network, and Convolutional Bayesian Kernel Inference (ConvBKI) to generate a 3D semantic map of the environment and provide accurate localization for the robot. The key innovation of our method is the real-time fusion of DROID-SLAM and Convolutional Bayesian Kernel Inference (ConvBKI), achieved through the introduction of point cloud generation from RGB-Depth frames and optimized camera poses. This integration, engineered to enable efficient and timely processing, minimizes lag and ensures effective performance of the system. Our approach facilitates functional real-time online semantic mapping with just camera images or stereo video input.

# # Summary. An optional shortened abstract.
# summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

tags:
- Perception
featured: false

# links:
# - name: ""
#   url: ""
url_pdf: https://www.oajaiml.com/uploads/archivepdf/85361173.pdf
url_code: 'https://github.com/peterstratton/Volume-DROID'
url_dataset: 'https://theairlab.org/tartanair-dataset/'
# url_poster: ''
# url_project: ''
# url_slides: ''
# url_source: ''
# url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
# image:
#   caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/jdD8gXaTZsc)'
#   focal_point: ""
#   preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
# projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
# slides: example
---

<!-- {{% callout note %}}
Click the *Cite* button above to demo the feature to enable visitors to import publication metadata into their reference management software.
{{% /callout %}}

{{% callout note %}}
Create your slides in Markdown - click the *Slides* button to check out the example.
{{% /callout %}}

Add the publication's **full text** or **supplementary notes** here. You can use rich formatting such as including [code, math, and images](https://docs.hugoblox.com/content/writing-markdown-latex/). -->

### Result
![screen render text](output.gif "Volume-DROID generating semantically laeled voxels")