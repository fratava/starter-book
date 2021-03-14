---
# Title, summary, and page position.
linktitle: Test
weight: 40

# Page metadata.
title: Test
date: "2020-12-31T00:00:00Z"
type: book  # Do not modify.
---

#  Probando nuestro clúster

## Aplicaciones en paralelo

### Llamada de procesos
Para esta parte, vamos a ejecutar una serie de códigos en parelelo para comprobar la comunicación entre los nodos. Para ello vamos a clonar el repositorio de pruebas siguiendo estos pasos:

```bash
su - alpha
cd /beta/
git clone https://gitlab.com/fratava/cluster-pi.git
cd cluster-pi
```

Para la primera prueba, vamos a comprobar que hay intercomunicación entre los nodos del clúster. Para evitar estar listando los núcleos que vamos a utilizar, crearemos una archivo en dónde le vamos a indicar a MPI los nodos con los cuales va a estalecer la comunicación dinámicamente. Es muy recomendable contar con este archivo, ya que de otra manera hay que indicarle explícitamente los núcleos de los nodos que vamos a utilizar. 

Creamos el archivo llamado `#!bash machinefile` de la siguiente manera

```bash
emacs machinefile
```

y escribimos

```bash
nodo1
nodo2
nodo3
master
```

pulsamos ctrl+s y ctrl+x. 

{{% callout info %}}
Si añadimos más nodos de cómputo a nuestro clúster o queremos hacer una segmentación, debemos modificar nuestro `machinefile` para agregar o remover nodos.
{{% /callout %}}

Compilamos el código 

```bash
mpicc call-procs.c -o call-procs
```

y los ejecutamos

Con machinefile
```bash
mpiexec -machinefile machinefile -n 16 ./call-procs
```

Sin machinefile
```bash
mpiexec -H master,master,master,master,nodo1,nodo1,nodo1,nodo1,nodo2,nodo2,nodo2,nodo2,nodo3,nodo3,nodo3,nodo3 ./call-procs
```

Si todo marcha bien debemos tener una salida como esta

```bash
Llamada al proceso 3 de 16 en master 
Llamada al proceso 2 de 16 en master 
Llamada al proceso 0 de 16 en master 
Llamada al proceso 1 de 16 en master 
Llamada al proceso 15 de 16 en nodo3 
Llamada al proceso 12 de 16 en nodo3 
Llamada al proceso 5 de 16 en nodo1 
Llamada al proceso 6 de 16 en nodo1 
Llamada al proceso 14 de 16 en nodo3 
Llamada al proceso 8 de 16 en nodo2 
Llamada al proceso 13 de 16 en nodo3 
Llamada al proceso 7 de 16 en nodo1 
Llamada al proceso 9 de 16 en nodo2 
Llamada al proceso 4 de 16 en nodo1 
Llamada al proceso 10 de 16 en nodo2 
Llamada al proceso 11 de 16 en nodo2 
```

Recordemos que las llamadas son aleatorias.

{{% callout info %}}
En algunas ocasiones, podrías no tener esta salida. En este caso deberás revisar que tu cable de red está bien conectado, tu raspberry está prendida o tu volumen está montado. Para verificar esto último podemos teclear
```bash
cd /beta
ls
```
Si el folder está vacío debemos teclear
```bash
sudo mount master:/beta /beta
```
y volvemos a ejecutar el código. 
{{% /callout %}}


### Calculando Pi en paralelo

Ahora calcularemos Pi de forma paralela. Para esto, haremos una integración numérica. La idea detrás de este algoritmo la podemos encontrar en esta [página](http://cercs-ed.gatech.edu/node/14).

Procedemos entonces a ejecutar el código. Primero lo compilamos

```bash
mpicc pi_mpi.c -o pi_mpi
```

y lo ejecutamos 

Con machinefile
```bash
mpiexec -machinefile machinefile -n 16 ./pi_mpi
```

Sin machinefile
```bash
mpiexec -H master,master,master,master,nodo1,nodo1,nodo1,nodo1,nodo2,nodo2,nodo2,nodo2,nodo3,nodo3,nodo3,nodo3 ./pi_mpi
```

En este caso no solicitará el número de rectángulos

```shell
#######################################################
Master node name: master 

Enter the number of intervals:
```

El valor queda al criterio del usuario. A continuación, te mostramos a modo de ilustración, los resultados que se obtienen para 300000 rectángulos cuando se calcula Pi con diferentes números de procesadores, los cuales los designaremos con "n=??" y `#!bash time` antes de la ejecución para medir el tiempo.

n=1
```shell
    alpha@master:/beta/cluster-pi $ time mpiexec -machinefile machinefile -n 1 ./pi_mpi

    #######################################################
    Master node name: master 

    Enter the number of intervals:

    300000


    *** Number of processes: 1 

    Pi Calculado = 3.141592653590713268840772798285
                Pi = 3.141592653589793115997963468544
    Error relativo = 0.000000000000920152842809329741

    real	8m54.547s
    user	8m47.000s
    sys	0m0.160s
```

n=2
```shell
    alpha@master:/beta/cluster-pi $ time mpiexec -machinefile machinefile -n 2 ./pi_mpi

    #######################################################
    Master node name: master 

    Enter the number of intervals:

    300000


    *** Number of processes: 2 

    Pi Calculado = 3.141592653590711492483933398034
                Pi = 3.141592653589793115997963468544
    Error relativo = 0.000000000000918376485969929490

    real	4m36.129s
    user	8m58.883s
    sys	0m0.211s
```

n=4
```shell
    alpha@master:/beta/cluster-pi $ time mpiexec -machinefile machinefile -n 4 ./pi_mpi

    #######################################################
    Master node name: nodo3 

    Enter the number of intervals:

    300000


    *** Number of processes: 4 

    Pi Calculado = 3.141592653590712824751562948222
                Pi = 3.141592653589793115997963468544
    Error relativo = 0.000000000000919708753599479678

    real	2m19.781s
    user	9m10.213s
    sys	0m0.228s
```

n=8
```shell
    alpha@master:/beta/cluster-pi $ time mpiexec -machinefile machinefile -n 8 ./pi_mpi

    #######################################################
    Master node name: master 

    Enter the number of intervals:

    300000


    *** Number of processes: 8 

    Pi Calculado = 3.141592653590715045197612198535
                Pi = 3.141592653589793115997963468544
    Error relativo = 0.000000000000921929199648729991

    real	1m26.563s
    user	4m44.188s
    sys	0m12.459s
```

n=16
```shell
    alpha@master:/beta/cluster-pi $ time mpiexec -machinefile machinefile -n 16 ./pi_mpi

    #######################################################
    Master node name: master 

    Enter the number of intervals:

    300000


    *** Number of processes: 16 

    Pi Calculado = 3.141592653590720818357340249349
                Pi = 3.141592653589793115997963468544
    Error relativo = 0.000000000000927702359376780805

    real	0m59.547s
    user	2m41.094s
    sys	0m30.697s
```

Como podemos darnos cuenta, el tiempo de ejecución, baja a medida que aumentamos el número de procesadores.

{{% callout success %}}
Ahora que tenemos nuestro clúster funcionando, desarrollaremos códigos parelelos. Pero como lo hemos mencionado en la [introducción](/introduccion/#en-que-se-utiliza-el-computo-de-alto-rendimiento), podemos utilizar nuestro clúster para diversas tareas. 
{{% /callout %}}