---
title: Kinich Pakal
summary: Atmósferas estelares en estrellas de tipo solar a longitudes de onda milimétricas y submilimétricas.
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

La atmósfera de las estrellas de tipo solar está compuesta por la fotosfera, la cromosfera, la zona de transición y la corona. La cromosfera es la capa donde la temperatura va de 4000 K a 8000 K y se estudia en longitudes de onda ultravioleta, visible, infrarroja, milimétrica y (sub) milimétrica (Wedemeyer et al. 2016) [^7].
Los primeros modelos cromosféricos se obtuvieron gracias a las observaciones ultravioleta (Vernazza et al. 1981; Avrett & Loeser 2008) [^6] [^1]. Sin embargo, observaciones recientes realizadas con el Telescopio Solar Submilimétrico (SST) y el Atacama Large Millimeter / Submillimeter Array (ALMA) han demostrado que la cromosfera tiene temperaturas más bajas de lo esperado por los modelos ultravioleta (Linsky 2017). [^2]

Hemos desarrollado el código KINICH-PAKAL (Tapia-Vázquez, & De la Luz 2020) [^5] que utiliza el algoritmo Levenberg-Marquard como método de ajuste no lineal, PAKAL-MPI como modelo cromosférico de la atmósfera solar y observaciones en longitudes de onda que van desde el infrarrojo al milímetro para generar un modelo más preciso de las cromosferas de las estrellas de tipo solar.
KINICH-PAKAL nos ha permitido estudiar en detalle cómo cambian las condiciones físicas de la atmósfera en función de su temperatura efectiva.
El desarrollo de estos modelos es necesario para estudios de discos de escombros (White et al. 2018) [^8], estudiar las condiciones bajo las cuales se forman las erupciones (MacGregor et al. 2018) [^4] y los posibles mecanismos físicos de variaciones de flujo en el estrellas (Liseau 2019) [^3].

### Referencias

[^1]: Avrett, E. H., & Loeser, R. 2008, ApJS, 175, 229.
[^2]: Linsky, J. L. 2017, ARA&A, 55, 159.
[^3]: Liseau, R. 2019, arXiv:1904.03043.
[^4]: MacGregor, M. A., Weinberger, A. J., Wilner, D. J., Kowalski, A. F., & Cranmer, S. R. 2018, ApJ, 855, L2.
[^5]: Tapia-Vázquez, F., & De la Luz, V. 2020, ApJS, 246, 5.
[^6]: Vernazza, J. E., Avrett, E. H., & Loeser, R. 1981, ApJS,45, 635.
[^7]: Wedemeyer, S., Bastian, T., Brajša, R., et al. 2016, SSRv, 200, 1.
[^8]: White, J.A., Aufdenberg, J., Boley, A.C., 2018, ApJ,859(2), p.102.
