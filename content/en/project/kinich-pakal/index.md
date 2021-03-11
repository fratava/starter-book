---
title: Kinich Pakal
summary: Main sequence stellar atmospheres at millimetric, submillimetric and infrared wavelengths.
tags:
- Estelar
- Radioastronomía
date: "2016-04-27T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: F. Tapia-Vázquez & De la Luz, 2020
  focal_point: Smart

links:
- icon: graduation-cap
  icon_pack: fas
  name: ADS
  url: https://ui.adsabs.harvard.edu/abs/2020ApJS..246....5T/abstract
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

The atmosphere of the Solar-like stars is composed of the photosphere, chromosphere, transition zone, and corona. The chromosphere is the layer where the temperature goes from 4000 K to 8000 K and is studied at ultraviolet, visible, infrared, millimeter and (sub)-millimeter wavelengths (Wedemeyer et al. 2016)[^7].
The first chromospheric models were obtained thanks to the ultraviolet observations (Vernazza et al. 1981; Avrett & Loeser 2008)[^6] [^1]. However, recent observations made with the Solar Submillimeter Telescope (SST) and the Atacama Large Millimeter / Submillimeter Array (ALMA) have shown that the chromosphere has lower temperatures than expected by ultraviolet models (Linsky 2017). [^2]

We have developed the KINICH-PAKAL (Tapia-Vázquez, & De la Luz 2020)[^5] code that use the Levenberg-Marquard algorithm as a nonlinear fit method, PAKAL-MPI as a chromospheric model of the solar atmosphere, and observations at wavelengths ranging from infrared to millimeter to generate a more accurate model of the chromospheres of the solar-type stars.
KINICH-PAKAL has allowed us to study in detail how the physical conditions of the atmosphere change as a function of its effective temperature.
Developing these models is necessary for debris disk studies (White et al. 2018)[^8], study the conditions under which flares are formed (MacGregor et al.2018)[^4] and the possible physical mechanisms of flux variations in the stars (Liseau 2019)[^3].

### References

[^1]: Avrett, E. H., & Loeser, R. 2008, ApJS, 175, 229.
[^2]: Linsky, J. L. 2017, ARA&A, 55, 159.
[^3]: Liseau, R. 2019, arXiv:1904.03043.
[^4]: MacGregor, M. A., Weinberger, A. J., Wilner, D. J., Kowalski, A. F., & Cranmer, S. R. 2018, ApJ, 855, L2.
[^5]: Tapia-Vázquez, F., & De la Luz, V. 2020, ApJS, 246, 5.
[^6]: Vernazza, J. E., Avrett, E. H., & Loeser, R. 1981, ApJS,45, 635.
[^7]: Wedemeyer, S., Bastian, T., Brajša, R., et al. 2016, SSRv, 200, 1.
[^8]: White, J.A., Aufdenberg, J., Boley, A.C., 2018, ApJ,859(2), p.102.
