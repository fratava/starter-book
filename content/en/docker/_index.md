---
# Title, summary, and page position.
linktitle: ¿Qué es Docker?
weight: 1

# Page metadata.
title: ¿Qué es Docker?
date: "2020-12-31T00:00:00Z"
type: book  # Do not modify.
---

Para entender lo que significa Docker, es necesario dar un breve repaso a los contenedores.

## ¿Qué es un contenedor?
Un contenedor o Container, es un sandbox donde es posible ejecutar servicios y procesos en un entorno protegido. Cada contenedor se ejecuta en un Host de Contenedor, que puede ser una máquina de Windows, MacOs o Linux. Los principales beneficios de los contenedores, si se comparan con las máquinas virtuales clásicas, son los siguientes: 

* La implementación es mucho más rápida.
* La administración es mínima.
* No es necesario aplicar parches y la huella es baja.


## ¿Por qué contenedores?
Los contenedores no son para todos y los escenarios no son muchos, en detalles:

* Sitios web
* Servicios
* Procesos
* Aplicaciones

Como servidor web, se puede utilizar el motor más importante, como IIS con .Net, Apache y Ngnix también; Como aplicación, podemos encontrar SQL Server para Windows o Linux y el motor de base de datos más importante.

En el ámbito científico, un contenedor nos proporciona una plataforma para crear escenarios avanzados que se pueden replicar fácilmente. En este sentido, un contenedor nos permite escalar códigos y adaptarlos a distintos tipos de infraestructura. Un punto importante para los desarrolladores de código, es que se pueden utilizar contenedores independientes para resolver los problemas de compatibilidad. Pensemos en el siguiente ejemplo. 

{{% callout note %}} Hemos desarrollado un código que resuelve numéricamente un sistema de ecuaciones. Nuestro código lo hemos desarrollado sobre un versión específica de fortran. Inicialmente los hemos compilado y probado en nuestra computadora y funciona correctamente. Llega el momento en que queremos compartir nuestro desarrollo con la comunidad científica, pero debemos enfrentarnos al reto de que no todo el mundo cuenta con el mismo compilador o peor aún, no todo el mundo está familiarizado con el sistema operativo. Esto hace muy dificil e incluso imposible, poder colaborar con los demás miembros de la comunidad. Entonces, nos interesaría encontrar una manera de portar el código, independientemente de la arquitectura del sistema o el sistema operativo de una manera fácil. {{% /callout %}}

## Docker

Cuando hablamos de contenedores, no podemos evitar hablar de Docker, quizás la plataforma de contenedores más conocida. Docker es una herramienta que está diseñada para beneficiar tanto a los desarrolladores como a los administradores de sistemas. Para los desarrolladores, significa que pueden centrarse en escribir código sin preocuparse por el sistema en el que finalmente se ejecutará. También les permite obtener una ventaja al usar uno de los miles de programas que ya están diseñados para ejecutarse en un contenedor Docker como parte de su aplicación. Para el personal de operaciones, Docker ofrece flexibilidad y reduce potencialmente la cantidad de sistemas necesarios debido a su tamaño reducido y menores gastos generales.

## ¿Por qué no utilizar una máquina virtual?

### ¿Qué es una máquina virtual?

Una máquina virtual es un sistema que actúa exactamente como una computadora.

En términos simples, hace posible ejecutar lo que parece estar en muchas computadoras separadas en hardware, es decir, una computadora. Cada máquina virtual requiere su sistema operativo subyacente y luego se virtualiza el hardware.

### Docker vs VM

Las diferencias significativas son la compatibilidad con el sistema operativo, la seguridad, la portabilidad y el rendimiento.


### Soporte del sistema operativo




El soporte del sistema operativo de la máquina virtual y el contenedor Docker es muy diferente. En la imagen de arriba, puede ver que cada máquina virtual tiene su sistema operativo invitado por encima del sistema operativo host, lo que hace que las máquinas virtuales sean pesadas. Mientras que, por otro lado, los contenedores Docker comparten el sistema operativo host, y es por eso que son livianos.

Compartir el sistema operativo host entre los contenedores los hace muy ligeros y les ayuda a iniciarse en solo unos segundos. Por lo tanto, la sobrecarga para administrar el sistema de contenedores es muy baja en comparación con la de las máquinas virtuales.

Los contenedores de la ventana acoplable son adecuados para situaciones en las que desea ejecutar varias aplicaciones en un solo kernel de sistema operativo. Pero si tiene aplicaciones o servidores que deben ejecutarse en diferentes tipos de sistemas operativos, entonces se requieren máquinas virtuales.

### Seguridad
La máquina virtual no comparte el sistema operativo y existe un fuerte aislamiento en el kernel del host. Por lo tanto, son más seguros en comparación con los contenedores. Un contenedor tiene muchos riesgos de seguridad y vulnerabilidades, ya que los contenedores tienen un núcleo de host compartido.

Además, dado que los recursos de la ventana acoplable se comparten y no tienen un espacio de nombres, un atacante puede explotar todos los contenedores de un clúster si obtiene acceso incluso a un contenedor. En una máquina virtual, no obtiene acceso directo a los recursos y el hipervisor está ahí para restringir el uso de recursos en una VM.

### Portabilidad
Los contenedores Docker son fácilmente portables porque no tienen sistemas operativos separados. Un contenedor se puede portar a un sistema operativo diferente y puede iniciarse inmediatamente. Por otro lado, las máquinas virtuales tienen sistemas operativos separados, por lo que portar una máquina virtual es difícil en comparación con los contenedores, y también lleva mucho tiempo portar una máquina virtual debido a su tamaño.

Para propósitos de desarrollo donde las aplicaciones deben desarrollarse y probarse en diferentes plataformas, los contenedores Docker son la opción ideal.

### Desempeño
Comparar las máquinas virtuales y los contenedores Docker no sería justo porque ambos se utilizan para diferentes propósitos. Pero la arquitectura ligera de Docker es característica que consume menos recursos lo convierte en una mejor opción que una máquina virtual. Como resultado, los contenedores pueden iniciarse muy rápido en comparación con el de las máquinas virtuales, y el uso de recursos varía según la carga o el tráfico en ellos.

A diferencia del caso de las máquinas virtuales, no es necesario asignar recursos de forma permanente a los contenedores. Escalar y duplicar los contenedores también es una tarea fácil en comparación con la de las máquinas virtuales, ya que no es necesario instalar un sistema operativo en ellas.

### Resumen

|                           Máquina virtual                          |                         Contenedor Docker                         |
|:------------------------------------------------------------------:|:-----------------------------------------------------------------:|
|             Aislamiento de procesos a nivel de hardware            |               Aislamiento de procesos a nivel de SO               |
|    Cada máquina virtual tiene un sistema operativo independiente   |                 Cada contenedor puede compartir SO                |
|                         Arranca en minutos                         |                        Arranca en segundos                        |
|               Las máquinas virtuales son de pocos GB               |              Los contenedores son livianos (KB / MB)              |
| Las máquinas virtuales listas para usar son difíciles de encontrar | Los contenedores Docker prediseñados están fácilmente disponibles |
| Las máquinas virtuales pueden moverse a un nuevo host fácilmente   | Los contenedores se destruyen y recrean en lugar de moverse       |
| La creación de VM lleva relativamente más tiempo                   | Los contenedores se pueden crear en segundos                      |
| Más uso de recursos                          