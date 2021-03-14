---
title: Configuranción de los nodos
linktitle: Configuranción de los nodos
type: book
date: "2020-12-31T03:00:00+01:00"
# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---


# Creando un usuario común

Para lograr que todos los nodos del clúster se puedan comunicar entre ellos, es necesario que cuenten con un usuario único. 

## Agregar un nuevo usuario

Para agregar un nuevo usuario, debemos teclear los siguientes comandos en el nodo maestro.

``` bash
cd /home
sudo useradd -m -u 1960 alpha
ls -la /home
```

El parámetro `-m` especifica el directorio `/home`, `-u` es el argumento para un nueevo usuario, 1960 es el ID del usuario y `alpha` es el nombre del nuevo usuario. Podemos modificar el nombre por otro. Al teclear ls -la /home aparecerá el nuevo usuario creado junto con `pi` y `root`.
El próximo paso, es crear un contraseña para este usuario. Teclamos entonces

``` bash
sudo passwd alpha
```

e introduciomos la contraseña.
Para verfificar que sea ha creado correctamente el usuario y que todo está en orden, vamos a iniciar sesión con el nuevo usuario coon el siguiente comando

``` bash
su - alpha
```

introducimos la contraseña y estamos dentro del usuario.  Si tecleamos 

``` bash
exit
```

regresamos al usuario `pi`. Ahora nos conectaremos mediante *ssh* al nodox y repetimos los pasos anteriores. Podemos acceder mediante 

```bash
ssh nodox
```

y ponemos la contraseña del nodo. 

{{% callout info %}}
Es bueno utilizar la misma contraseña para todos los nodos.
{{% /callout %}}

## Generar el ID key

Ahora que ya configuramos el usuario en común, el nodox va a correr todos los programas MPI. Vamos a generar un llave especial que permitirá conectarnos mediante *ssh* sin contraseña de un nodo a otro, o del nodo maestro a un nodo las veces que lo necesitemos. Para hacer esto nos situamos en el nodo maestro y después, nos conectamos al usuario *alpha* mediante 

``` bash
su - alpha
```

y una vez adentro, teclamos los siguiente

``` bash
ssh-keygen -t rsa
```

en donde `-t` es el argumento y `rsa` es el tipo de encriptación. Para generar la clave necesitamos ingresar 

* El nombre del archivo donde vamos a guardar la clave
* Ingresar la *passphrase* (escogeremos la frase de nuestra elección)
* Reingresamos la *passphrase*

y tendremos que ver una imagen como la siguiente

``` bash
+--[ RSA 2048]----+
|       o=.       |
|    o  o++E      |
|   + . Ooo.      |
|    + O B..      |
|     = *S.       |
|      o          |
|                 |
|                 |
|                 |
+-----------------+
```

## Copiar la clave a los demás nodos

Ya que generamos la clave, la vamos a transferir al nodox con el siguiente comando

```bash
ssh-copy-id alpha@nodox; alpha
```

y teclamos el *passphrase*. Para verificar que se tranfirió bien la clave, nos conectaremos al nodo de la siguiente manera

```bash
ssh nodox
```

e introducimos el *passphrase* nuevamente e ingresaremos al nodox. Ahora regresamos al nodo maestro mediante `exit` y listamos los archivos en el usuario alpha utilizando `ls -la`. Indentificamos la carpeta `.ssh` y vemos lo que está adentro con `ls -la .ssh`. Ahí vamos a ver estos tres archivos

* id_rsa
* id_rsa.pub
* known_hosts

Si nos intentamos conectar nuevamente al nodox, nos va a solicitar la *passphrase*. Esto no es lo que estamos buscando, por lo que aún debemos realizar algunos cambios en nuestro nodo maestro. Regresamos al nodo maestro mediante `exit` o cerrando la ventana de la terminal y conectandonos al modo maestro. Nos percatamos que nos encontramos en el usurio `alpha`, si no es así ingresamos mediante `su - alpha`. Vamos a editar el archivo llamado `.bashrc` dentro de nuestro directorio de inicio. Abrimos el archivo con nuestro editor favorito, puede ser emacs, vim, nano o pico. Nano viene instalado por defecto, entonces lo utilizaremos en esta guía. Entonces teclamos 

```bash
nano .bash
```

nos vamos hasta el final del archivo y agregamos el siguiente texto

```bash
#Logic for keychain
/usr/bin/keychain $HOME/.ssh/id_rsa
source $HOME/.keychain/$HOSTNAME-sh
```

y tecleamos `ctrl + o` para guardar y `ctrl + x` para salir. Entonces recompilamos el archivo `.bashrc` mediante 

```bash
source .bashrc
```

volvemos a ingresar el *passphrase*. Ahora nos volvemos a conectar al nodox con

``` bash
ssh nodox
```

y ¡listo!, nos hemos conectado al nodox. Vamos a repetir este proceso para cada nodo del clúster.

## Creando una carpeta compartida

Para que los datos puedan ser accesibles para todos los nodos, es necesario crear un repositorio. Vamos a montarlo en el nodo maestro de la siguiente manera. Primero, vamos a crear la carpeta que va a ser compartida.

``` bash
sudo mkdir /beta
```

en este caso la montanmos en el directorio raíz `/` y la llamaremos beta. Le cederemos la propiedad al usuario `alpha`, ya que es el usuario común. Entonces tecleamos

```bash
sudo chown alpha:alpha /beta/
```

el directorio `/beta` ahora puede ser accedido por el usuario y grupo `alpha`. El siguiente paso es modificar el servicio `rpcbind` para poder exportar el directorio a los demás nodos. tecleamos 

``` bash
sudo rpcbind start
sudo update-rc.d rpcbind enable
```

la segunda línea es para especificar que el servicio se ejecute cada vez que se inicia el sistema. Tenemos ahora que especificar que directorio en el nodo maestro va a estar disponible para ser montado por los demás nodos. Para ellos vamos a modificar el archivo `exports` abriendolo con `sudo emacs /etc/exports` ya añadiendo al final del archivo la siguiente línea

``` bash
#beta
/beta 192.168.0.0/24(rw,sync)
```
Salvamos con `ctrl+x+ctrl+s` y salimos con `ctrl+x+ctrl+c`.

En este caso `/beta`es la carpeta en el nodo maestro que vamos a exportar. `192.168.0.0/24` significa que las direcciones IP pueden en un rango entre `192.168.0.0` y `192.168.0.255` pueden montar el directorio `/beta`. `rw` significa que se puede leer y escribir en ella. Para que tenga efecto el cambio que realizamos, necesitamos reiniciar el servicio `nfs-kernel-server`con `sudo service nfs-kernel-server restart`. Se puede automatizar este proceso cada vez que inicie el sistema. Para ello necesitamos mofdificar el archivo `sudo emacs /etc/rc.local` y poner en la penúltima línea, antes de `exit 0` lo sigueinte

``` bash
sudo service nfs-kernel-server restart
```

guardamos y cerramos el archivo. Vamos a hacer un test. Nos conectamos al nodox con `ssh nodox` y una vez dentro, teclamos los siguiente

``` bash
sudo mkdir /beta
sudo chown alpha:alpha /beta
sudo mount master:/beta /beta
````

hemos creado un directorio llamado `\beta` que ahora le pertenece al usuario y al grupo `alpha`. Después, le indicamos que monte el directorio `/beta` del `master` en `/beta`. Para probar que todo ha sido ejecutado de manera correcta, vamos a cambiar al usuario `alpha` con `su - alpha`. Para ver los directorio que se encuentran en la carpeta raíz hacemos `la -la /` y debe aparecer `/beta`, nos cambiamos a ese directorio con `cd /beta` y creamos un archivo `echo "Hola mundo" -> hola.txt`. Regresamos al usuario `pi`con `exit` y ahora nos conectamos de vuelta al nodo maestro `ssh master`. Una vez en el nodo maestro podemos ver si el archivo se ha guardado en el directorio compartido con `ls -la /beta`. Ahí debe aparecer el archivo `hola.txt`y si hacemos `cat /beta/hola.txt` nos debe aparecer la frase `Hola mundo`.

{{% callout success %}}
Hemos configuirado nuestro clúster de manera correcta. En la siguiente sección, vamos a hacer algunas pruebas.
{{% /callout %}}

<!--- <iframe src="https://drive.google.com/file/d/107aUt0Pp2Ud-JUl-VkmFnw0Lq4iv0ALH/preview" width="640" height="480" aling="center"></iframe>  --->

