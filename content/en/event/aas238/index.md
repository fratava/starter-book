---
title: Modeling Altair’s Atmosphere

event: 238th Meeting of the American Astronomical Society
event_url: https://aas.org/meetings/aas238

location: Virtual Meeting
#address:
#  street: 450 Serra Mall
#  city: Stanford
#  region: CA
#  postcode: '94305'
#  country: United States

summary: Presentation No.116.01 in the session “Stellar Atmospheres and Winds”.
abstract: "Stellar emission at infrared to centimeter wavelengths remains largely unconstrained since only a few stars other than the Sun have been observed at these wavelengths. This lack of observations means that radio stellar atmosphere models cannot be informed by data. In this work, we present a new methodology to fit the observed and synthetic spectrum of Altair through semiempirical models. We adapt both KINICH-PAKAL and PHOENIX models to reproduce Altair's radio spectra. KINICH-PAKAL is a new framework that allows adapting a solar chromospheric model to solar-like stars iteratively. KINICH-PAKAL uses the Levenberg-Marquardt algorithm as a Nonlinear method, PakalMPI as the semiempirical model, and the observations at infrared to centimeter wavelengths. Our results show that both PHOENIX and KINICH-PAKAL model reproduces the photosphere and lower chromosphere. However, the KINICH-PAKAL features allow to better model the part of the spectrum where the upper chromosphere and the corona have the major contribution. These results are part of an on-going observational campaign called The MESAS Project which seeks to Measure the Emission of Stellar Atmosphere at Submillimeter to millimeter wavelengths."

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: "2021-06-07T09:00:00Z"
date_end: "2021-06-09T18:00:00Z"
all_day: false

# Schedule page publish date (NOT talk date).
publishDate: "2017-01-01T00:00:00Z"

authors:
- admin
- White, J
- Hughes, A.G
- Moór, A
- Matthews, B
- Wilner, D
- Aufdenberg, J
- Fehér, O
- Hughes, A.M
- De la Luz, V
- McNaughton, A
- Zapata, L

tags:
- AAS238
featured: true

image:
  caption: 'White et al. 2021'
  focal_point: Right

links:
- icon: twitter
  icon_pack: fab
  name: Jacob on Twitter
  url: https://twitter.com/Jacob_White26
url_code: ""
url_pdf: ""
url_slides: https://keynotes.ftapia.dev/aas238
url_video: ""

# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects:
- kinich-pakal
- mesas
---