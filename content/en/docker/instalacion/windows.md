---
title: Instalando Docker en Windows
linktitle: Instalando Docker en Windows
type: book
date: "2020-12-31T00:00:00+01:00"
# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

Ahora que sabemos lo que es docker, vamos a instalarlo en nuestra computadora. Antes de instalarlo, es recomendable actualizar nuestro Windows a la versión más actual.

Opcionalmente, podemos instalar algunos programas que nos ayudarán a tner una mejor experiencia de uso. Si ya tienes instalados estos programas, puedes dirigirte a la sección --.


## Instalación de software esencial

### La terminal de Windows

Para poder interactuar con docker, es necesario tener instalado una terminal. Podemos utilizar la terminal que por defecto tiene Windows, pero es altamente recomendable instalar la nueva versión. Para obtenerla, sólo tenemos que ir a la Microsoft Store y buscar "Windows terminal". Y descargamos la primer aplicación. A continuación, te muestro como hacerlo desde Windows 10.


{{< youtube MFwPGXUnD60 >}}

### Git

Para trabajar con proyectos open source, es bastante recomendable trabajar con un control de versiones. Git es un software diseñado por Linus Torvalds para este fin. Puede que te preguntes, ¿qué es un control de versiones? Bueno, podemos definirlo como una gestión de los diversos cambios que se realizan sobre los elementos de algún producto o configuración. Una versión, revisión o edición de un producto, es el estado en el que se encuentra el mismo en un momento dado de su desarrollo o modificación. Aunque un sistema de control de versiones puede realizarse de forma manual, es mejor disponer de herramientas que faciliten esta gestión dando lugar a los llamados sistemas de control de versiones o VCS (del inglés Version Control System). Estos sistemas facilitan la administración de las distintas versiones de cada producto desarrollado, así como las posibles especializaciones realizadas (por ejemplo, para algún cliente específico). Sii te interesa conocer más a detalle como funciona el control de versiones, puedes visitar este [link](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Acerca-del-Control-de-Versiones).

En el siguiente videos te muestro cómo puedes descargar git en Windows 10.

{{< youtube jyTEZOVTP4Q >}}

Para comprobar que está activo git, puedes seguir los pasos del siguiente video.

{{< youtube zJeUsW3m5k0 >}}

### Xming

Para poder desplegar aplicaciones gráficas desde un contenerdor docker, es necesario contar con un servidor gráfico. Pero, ¿qué es un servidor gráfico? Un servidor gráfico o servidor de ventanas es un programa cuya tarea principal es coordinar la entrada y la salida de sus clientes hacia y desde el resto del sistema operativo, el hardware, y otros. El servidor gráfico se comunica con sus clientes con el protocolo de servidor gráfico. Un protocolo de comunicaciones que puede ser transparente a la red o simplemente con capacidad para usar la red[^1]. Actualmente existe varios servidores gráficos, pero son dos los más populares, X11 (X.Org) y Wayland. En el siguiente video, te explico como instalar X11 en Windows 10.

{{< youtube c0AaSZkC4Z4 >}}

### Activar Hyper-V

Para poder asignar recursos computacionales, es necesario hacer una virtualización. Windows ofrece una herramienta llamada Hyper-V. Para poder ejecutar docker correctamente, es necesario instalarla. En el siguiente video te muestro como hacerlo.

{{< youtube Tex926ZukcY >}}

### Instalar WSL2 

Otra herramienta indipensable para poder ejecutar docker es Windows Subsystem for Linux (WSL). WSL, permiite ejecutar un amboiente GNU/Linux directamente en Windows, sin necesidad de instlar una máquina virtual tradicional como VM o un hacer un dual boot. En este video te muestro como instalar WSL2. Si quieres saber más, puedes ir a este [link](https://docs.microsoft.com/en-us/windows/wsl/about).

{{< youtube 24_RgbhYcvs >}}

## Instalando Docker

Finalmente, procederemos a instlar docker. A continuación te explico los pasos a seguir.

{{< youtube wOqxqhwPDFU >}}

### Verificando la instalación de docker

Vamos a verificar que la instalación de docker está bien. Para ello vamos a ejecutar la imagen de bienvenida a docker como se muestra en el video.

{{< youtube LGt3ABDEel8 >}}

[^1]: Artículo de Wikipedia [link](https://es.wikipedia.org/wiki/Servidor_gr%C3%A1fico)