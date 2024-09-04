---
title: Extension of Region-based Semantic Factorization in GANs (ReSeFa) to animal faces
summary: Reproduced ReSeFa to factorize latent space semantics for regions of interest for human faces and extended ReSeFa for editing animal faces  
# tags:
#   - Hardware
date: '2024-06-20T00:00:00Z'

# # Optional external URL for project (replaces project detail page).
# external_link: 'https://drive.google.com/drive/folders/1QiKoDUbkspXU7acjHh91cRRhuZhNsnxe'

# image:
#   caption: Process Overview
#   focal_point: Smart

links:
  - name: Report
    url: https://drive.google.com/file/d/14Nf5hCzYj_SltjBX_kCEjnWZ5gb-fNpy/view?usp=drive_link
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

The Generative Adversarial Networks (GANs) architecture involves two sub‐models: a generator model for generating new samples and a discriminator model for classifying the generated samples as real and fake. These sub‐models are trained together in a zero‐sum game manner, thus adversarial in nature. The generator takes a random vector with a fixed length as input and generates a sample. This generated sample vector is referred to as latent code, and the space of vectors is referred to as latent space. In essence, the generator model learns the mapping from the latent space to the image space of the dataset, for training the GANs. Conventional methodw perform this mapping mechanism but cannot locally edit the regions of interest (RoI), in other words didn't find semantically meaningful directions. A meaningful semantic direction in the latent code is a direction in the latent space that corresponds to a meaningful change in the generated images for targeted RoI.

The following claims of the author were verified during reimplementation,
‐ ReSeFa doesn’t require detailed spatial masks. A rough bounding box is sufficient to define the region of interest.
‐ The process of finding latent directions using ReSeFa focuses on solving an eigen‐decomposition problem, gaining independence from model structures.
‐ ReSeFa induces flexibility as it can be generalized to various GAN models.
‐ ReSeFa realizes quick implementation and precise editing of regions of interest.
 
ReSeFa uses the StyleGAN2 model pre‐trained on the Flickr‐Faces‐HQ (FFHQ) dataset to produce high‐resolution images. Besides, we also use the StyleGAN3 pre‐trained on the Animal Faces‐HQ (AFHQ) dataset. The degree of editing $\alpha$ is the hyperparameter that influences the manipulated image generation process. As stated above we intend to find the latent direction $n \in \mathbb{Z}$ in such a way that altering a latent code $z$ through the direction can cause
the corresponding semantic change in the manipulated image $x$.

$$edit(x) \triangleq x^{edit} = G(z + \alpha n)$$

The coordinates of the RoI and the indices of the feature layers chosen to manipulate from hierarchical feature layers are the hyperparameters that influence the direction discovery process.

### Reproduced qualitative results
![screen render text](resafa.png "Comparison of precise local editing results produced in the original paper and our reimplementation of the original paper. The RoI is highlighted in green boxes while all the rows share the same latent directions")

### Extended qualitative results
![screen render text](afhqq.png "Qualitative Results from ReSeFa with StyleGAN3 pre‐trained on AFHQ")

<!-- ![screen render text](tejas.gif "360° maneuverability highlighting sideways and diagonal movements at client's shopfloor bearing 500kg payload") -->

<!-- {{< video src="tejas.mp4" controls="yes" >}}
360° maneuverability highlighting sideways and diagonal movements at client's shopfloor bearing 500kg payload -->

<!-- #### Photo Gallery
{{< gallery album="hbr" >}} -->