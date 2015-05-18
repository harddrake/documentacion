# GNU/Linux

## Comandos basicos

* listar archvios
```
ls -l (listado de archivos con el dueño)
```
resultado del comando
```
total 32
drwxr-xr-x 2 feryan feryan 4096 may 13 02:02 Descargas
drwxr-xr-x 2 feryan feryan 4096 may 13 07:53 Documentos
drwxr-xr-x 2 feryan feryan 4096 may 13 02:02 Escritorio
drwxr-xr-x 2 feryan feryan 4096 may 13 02:02 Imágenes
drwxr-xr-x 2 feryan feryan 4096 may 13 02:02 Música
drwxr-xr-x 2 feryan feryan 4096 may 13 02:02 Plantillas
drwxr-xr-x 2 feryan feryan 4096 may 13 02:02 Público
drwxr-xr-x 2 feryan feryan 4096 may 13 02:02 Vídeos
```

* listar archivos, ordenar por fecha de modificacion

```
ls -lahtr
```

* crear directorios 

```
mkdir nombre_carpeta
```

```
mkdir -p /nombre_carpeta/subcarpeta
```

* crea varios subdirectorios de una sola instruccion

```
mkdir /tmp/{c1,c2,c3,c4,c5,c6}
```

```
mkdir -p /dir/qqq/aaa/bbbb/{c1,c2,c3,c4,c5,c6}
```

```
. (punto) Directorio actual
~ Home del usuario
```

```
mkdir ./hola/
```

```
mkdir ~/hola/ 
```

* crear un archivo vacio

```
touch nombre_archivo (tipo texto plano)
```

* Para editar archivos

```
nano, vi, vim, etc
```

* Crear archivo a partir del resultado de un comando se usa el simbolo ">", ">>" para concatenar elresultado.

* Para buscar dentro de un archivo 

```
grep texto nombre_archivo
```

* para que te despliegue el numero de la linea

```
grep -n texto nombre archivo
```

* para buscar en todo un directorio

```
grep -nR aa . > resultado.txt
```

* Buscar archivo dentro de un directorio

```
find directorio -name nombre_archivo^Carpeta
```

* buscar archivo sin conocer extension
```
find directorio -name nombre_arhchivo\*
```
el \* es como comodin

* Para conocer el manual de un comando

```
man nombre_comando
```

* conocer donde esta los arhivos de un determinado comando

```
whereis nombre_comando
```

* borar archivos

```
rm nombre_archivo
```

* borar archivo de forma recursiva

```
rm -r nombre_archivo
```

* ejecutar con privilegios de administrador

```
sudo mkdir /opt/bbb
```

* para ingresar o salir a una carpeta o directorio

```
cd nombre_carpeta
```

* se puede ingresar o salir de un subdirectorio directamente

```
cd /a/b/c/d/f/g/h/i/j/k
```

```
cd /a/b/c/d/f/g/h/i/j/k /../../../
```

```
cd ~
```

* para instalar paquetes

```
apt-get install nombre_paquete
```

```
aptitude install nombre_paquete
```

* Archivo para configurar repositorio

```
/etc/apt/source.list
```

* Instalar paquete sudo

```
apt-get install sudo
```

* comando groups

```
groups
```

* agregar usuario a un grupo (como root)

```
adduser nombre_usuario nombre_grupo
```

* para ver nuestras tarjetas de red

```
lspci | grep -i network
```

```
lspci | grep -i ethernet
```

* para ver si el driver esta en el repositorio

```
aptitude search nombre_driver
```

* instalacion de GIT

```
apt-get install git
```





## Virtualizacion

### Virtualizacion completa - KVM

### Virtualizacion ligera - LXC, Docket

