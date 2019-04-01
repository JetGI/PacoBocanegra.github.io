## Introdución
Para esta práctica hemos usado un ubuntu server 18.04 para realizar la instalacion de **JEKYLL**.

## Instalación

En primer lugar hemos añadido al fichero **/etc/apt/source.list** en la primera línea, el parámetro **universe**.

Una vez hecho esto, actualizamos con apt update.

```sh
$ sudo apt update
```

Cuando se termine de actualizar, debemos instalar los siguientes paquetes: “ruby-full build-essential zlib1g-dev”

```sh
$ sudo apt-get install ruby-full build-essential zlib1g-dev
```
Una vez instalados, debemos incluir unas variables en el fichero oculto **~/.bashrc**. Este fichero es el responsables que las variables del usuario se carger al iniciar sesión, por lo cual editando este fichero conseguiremos que las variables se cargen al inicio de sesión del usuario.

```sh
$ echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
$ echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
$ source ~/.bashrc
```
Lo siguiente será instalar la gema de jekyll.

```sh
$ gem install jekyll bundler
```

Una vez instalada la gema, debemos generar nuestro sitio.

```sh
$ jekyll sitio bundler
```
Entramos en el directorio del sitio que hemos creado.

```sh
$ cd sitio
```
Iniciamos el servidor en local (127.0.0.1):

```sh
$ bundle exec jekyll serve
```
Para poder acceder desde el exterior, utilizamos el siguiente comando.

*bundle exec jekyll serve --host={ip_de_nuestro_server}*

**Ejemplo:**

```sh
$ bundle exec jekyll serve --host=192.168.128.176
```

Para crear un nuevo post deberemos hacer lo siguiente:

Nos dirigimos a la carpeta "~/sitio/_post" (En nuestro caso se encuentra en esta ruta).

Creamos un fichero el cual debe contener la siguiente estructura.

**YYYY-MM-DD-titulo.md**

**2019-03-08-nuevo-post.md** o **2019-03-08-prueba.markdown**

Dentro de 2019-03-08-prueba.markdown deberemos tener el siguiente contenido.
```
---                                 → Apertura
layout: post                        → Diseño 
title: "Post Grupal"                → Título de post
date: 2019-03-08 13:29:00 +0000     → Fecha y hora
categories: jekyll update           → Categorías
---                                 → Cierre

```
Información que deseéis poner, como por ejemplo, bienvenidos. 
