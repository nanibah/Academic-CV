---
title: "Automation of Vehicle Door"
authors:
- Shalikha R
- admin
- Puhazhmathi M
- Suresh M
date: "2020-01-28T00:00:00Z"
# doi: " https://doi.org/10.34256/irjat2011"

# Schedule page publish date (NOT publication's date).
publishDate: "2020-01-28T00:00:00Z"

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
# publication_types: ["article"] - preprint
publication_types: ["article-journal"]

# Publication name and optional abbreviated publication name.
publication: "International Research Journal of Automotive Technology, Maple Tree Journals"
publication_short: "IRJAT"

abstract: In this paper, we have implemented the concept of automatic sliding door in public transport focusing on the safety of the passengers. The objective is to design a simple, effective and economic automatic sliding door system. Pneumatic cylinders, direction control valves and optical proximity sensor has been used to design the circuit. 

# # Summary. An optional shortened abstract.
# summary: Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis posuere tellus ac convallis placerat. Proin tincidunt magna sed ex sollicitudin condimentum.

# tags:
# - Source Themes
# featured: false

links:
# - name: Custom Link
#   url: http://example.org
url_pdf: https://www.researchgate.net/publication/340970266_Automation_of_Vehicle_Door
# url_code: 'https://github.com/HugoBlox/hugo-blox-builder'
# url_dataset: '#'
# url_poster: '#'
# url_project: ''
# url_slides: ''
# url_source: '#'
# url_video: '#'

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
# image:
#   caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/s9CC2SKySJM)'
#   focal_point: ""
#   preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
# projects:
# - internal-project

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
# slides: example
---

<!-- {{% callout note %}}
Create your slides in Markdown - click the *Slides* button to check out the example.
{{% /callout %}}

Add the publication's **full text** or **supplementary notes** here. You can use rich formatting such as including [code, math, and images](https://docs.hugoblox.com/content/writing-markdown-latex/). -->

### Technical Overview
Compressed air is provided to the system only when the vehicle driver provides control utilizing a push button or a mechanical lever and the door open. An optical proximity switch is used to detect the movement of the passengers. When the passenger enters or leaves from the vehicle, an electrical signal from the sensor is sent to the solenoid.This signal acts as a pilot for component #3, which keeps the door open.  

When the compressed air is supplied to the entire system, the time delay valve starts. Once the time is delayed, the the door starts closing. Whenever a signal from the optical proximity switch is received, the timer resets, ensuring the safety of the passengers. Once the time is delayed, a roller operated, spring return 3/2 DCV acts as a limit switch to ensure that the door is closed. This signal acts as a pilot to reset the driver control and the system is back to its initial state.
