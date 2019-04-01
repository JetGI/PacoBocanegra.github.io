## Introducción
Realizaremos una instalacion de el gesto de paquete yourt para ArchLinux el cual hace uso de los repositorio AUR (Arch User Repository).

## Instalación de yaourt

Para empezar abriremos la terminal o consola y procederemos con los siguientes comandos:
```sh
sudo pacman -Syu
sudo pacman -S git
```
Acto seguido clonamos el repositorio query:

```sh
git clone https://aur.archlinux.org/package-query.git
cd package-query
makepkg -si
```
Y continuamos con el clonado del repositorio de yaourt:

```sh 
git clone https://aur.archlinux.org/package-query.git
cd package-query
makepkg -si
```

Y continuamos con el clonado del repositorio de yaourt:

```sh
cd ..
git clone https://aur.archlinux.org/yaourt.git
cd yaourt
makepkg -si
```
Por último desinstalaremos los paquetes  para proceder posteriormente a su instalación si es que los teníamos previamente en el sistema:

```sh
cd ..
rm -rf yaourt package-query
```

Para acabar actualizaremos el sistema e instalaremos los paquetes del repositorio clonado con el siguiente comando:

```sh
yaourt -Syy
```

[Web](https://lignux.com/como-instalar-yaourt-en-arch-linux-y-derivadas-tips-junio-2018/)
