---
# Title, summary, and page position.
linktitle: Evaluación inicial
summary: Learn how to use Academic's docs layout for publishing online courses, software documentation, and tutorials.
weight: 1
icon: book
icon_pack: fas

# Page metadata.
title: Evaluación inicial
date: "2021-03-01T00:00:00Z"
type: book  # Do not modify.
---

{{< gdocs src="https://drive.google.com/file/d/1gHBQAbpW9ysxYT7qrWiCdXDVjBwAOgcN/preview" >}}


## Respuestas al ejercicio

> Ejercicio: Dentro de una bolsa se encuentran 20 monedas, 8 de ellas son de $5, el resto son de distintas denominaciones.

### Pregunta 1

> Calcula la probabilidad de sacar una moneda de $5 de la bolsa

$$ P($5)=\frac{8}{20}=\frac{2}{5}=0.4 $$

### Pregunta 2

> Calcula la probabilidad de conseguir al menos una moneda de $5 al sacar dos monedas de la bolsa.

#### Forma 1

P(al menos una moneda $5)=P($5 y otra denominación)+P(otra denominación y $5)+P($5 y $5)

$$ P(x\geq1)=\frac{8}{20}.\frac{12}{19}+\frac{12}{20}.\frac{8}{19}+\frac{8}{20}.\frac{7}{19}=\frac{24}{95}+\frac{24}{95}+\frac{14}{95}=\frac{62}{95}=0.65 $$

#### Forma 2

P(al menos una moneda 5) = 1 - P(no salga ninguna moneda de $5)

$$ P(x\geq1)=1-P(x=0)=1-\frac{12}{20}.\frac{11}{19}=1-\frac{33}{95}=\frac{62}{95}=0.65 $$


### Pregunta 3

>Calcula la probabilidad de conseguir al menos una moneda de $5 al sacar tres monedas de la bolsa.

$$ P(x\geq1)=1-P(x=0)=1-\frac{12}{20}.\frac{11}{19}.\frac{10}{18}=1-\frac{11}{57}=\frac{46}{57}=0.8 $$