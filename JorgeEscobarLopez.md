# GNU/Linux

## Accesos directos de terminal
```
CTRL L = Clear the terminal
CTRL D = Logout
SHIFT Page Up/Down = Go up/down the terminal
CTRL A = Cursor to start of line
CTRL E = Cursor the end of line
CTRL U = Delete left of the cursor
CTRL K = Delete right of the cursor
CTRL W = Delete word on the left
CTRL Y = Paste (after CTRL U,K or W)
TAB = auto completion of file or command
CTRL R = reverse search history
!! = repeat last command
```
## Comandos basicos

```
ls -a = lista todos los archivos y carpetas incluso archivos y carpetas ocultas
ls <NombreCarpeta> = lista archivos en el folderfiles in folder
ls -lh = Listado Detallado
ls -l *.jpg = Lista solo los archivos jpeg
ls -lh <NombreArchivo> = Resultado para un solo archivo
du -h: Uso de disco por las carpetas
du -sh: Muestra solo el disco utilizado por las carpetas
pwd = Muestra el directorio de trabajo

```
resultado del comando:
```
jorge@linux-68lz:~> ls -lh
total 60K
drwxr-xr-x  2 jorge users 4,0K may 23 21:50 bin
drwxr-xr-x  2 jorge users 4,0K may 27 21:30 Descargas
drwxr-xr-x  3 jorge users 4,0K may 26 14:45 Documentos
drwxr-xr-x  2 jorge users 4,0K may 27 10:11 dwhelper
drwxr-xr-x  2 jorge users 4,0K may 23 22:06 Escritorio
drwxr-xr-x  2 jorge users 4,0K may 26 15:24 Imágenes
drwxr-xr-x  5 jorge users 4,0K may 26 23:01 Música
drwxr-xr-x  2 jorge users 4,0K may 23 22:05 Plantillas
drwxr-xr-x  3 jorge users 4,0K may 26 21:20 pruebas
drwxr-xr-x  2 jorge users 4,0K may 23 21:50 public_html
drwxr-xr-x  2 jorge users 4,0K may 23 22:05 Público
drwxr-xr-x  6 jorge users 4,0K may 27 07:35 test
drwxr-xr-x  2 jorge users 4,0K may 23 22:05 Vídeos
drwxr-xr-x 10 jorge users 4,0K may 26 21:44 virtual-drives
drwxr-xr-x  2 jorge users 4,0K may 25 17:56 Virtuales

```

##listar archivos, ordenar por fecha de modificación

```
ls -lahtr
```

# Manipulación básica

cat <NombreArchivo> = Muestra el contenido de un archivo
(less, more)
head = Muestra el archivo desde el inicio
-n <#delineas> <NombreArchivo>
tail = Muestra el archivo desde el final
-n <#delineas> <NombreArchivo>
mkdir = Crea un nuevo directorio

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
##Comando cp
```
cp imagen.jpg nuevaimagen.jpg = copia y renombra un archivo
cp imagen.jpg <directorio>/ = copy to folder
cp imagen.jpg directorio/archivo2.jpg
cp *.txt stuff/ = copia todo de  *<tipo de archivo> a un directorio
```
##Comando mv
```
mv archivo.txt Documentos/ = mueve el archivo a un directorio
mv <directorio> <directorio2> = mueve un directorio en otro directorio
mv archivo.txt archivo2.txt = renombra un archivo
mv <directorio>/ .. = mueve el directorio un nivel más arriba en la jerarquía
```
##Comando rm
```
rm <archivo> .. = elimina archivo (s)
rm -i <archivo> .. = solicita confirmación por cada archivo
rm -f <archivo> = fuerza la eliminación de un archivo
rm -r <directorio>/ = elimina directorio
```
##Crear un archivo vacio

```
touch <fileName> = crea o actualiza un archivo de texto (tipo texto plano)

```

##Editores de archivos

```
nano, vi, vim, gedit, kwrite, etc
```

* Crear archivo a partir del resultado de un comando se usa el simbolo ">", ">>" para concatenar elresultado.

##Para buscar dentro de un archivo

```
grep texto nombre_archivo
```

##Para que te despliegue el numero de la linea

```
grep -n texto nombre archivo
```

Para buscar en todo un directorio

```
grep -nR aa . > resultado.txt
```

Buscar archivo dentro de un directorio

```
find directorio -name nombre_archivo^Carpeta
```

Buscar archivo sin conocer extension
```
find directorio -name nombre_archivo\*
```
el \* es como comodin

## Manual de un comando

```
man nombre_comando
```

## whereis conocer la ruta de un arhivo

```
whereis nombre_archivo
```

* ejecutar con privilegios de administrador

```
sudo mkdir /opt/bbb
```

## Moverse por los directorios

```
cd nombre_carpeta
cd <NombreCarpeta> = Cambia de directorio
cd / = Va hacia la raiz
cd .. = un nivel hacia arriba de una directorio
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

#Convetir paquetes .deb a .rpm para opensuse 13.2

aqui cinco pasos para instalar  Haroopad en openSUSE 13.2.

I tested it on a 32 bit rig, the process should be the same for a 64 bit building, and changing the zypper commands with the corresponding yum commands, it should work on Fedora too.

First, we need Haroopad, we can dowload the .deb version suitable for our achitecture here: http://pad.haroopress.com/user.html

Second, we need alien, a tool capable to convert .deb packages to .rpm packages: it is not available in the official repos.

We add the utilities repo and refresh:
Adicionamos utilidades y refrescamos los repositorios
```
sudo zypper ar -f http://download.opensuse.org/repositories/utilities/openSUSE_13.2/utilities.repo
```
```
sudo zypper ref
```
Then we install alien and the basic rpm building tools:
```
sudo zypper in rpm-build alien
```
Third, we build the .rpm file from the .deb file we downloaded in the first step using alien:
```
alien -r -c haroopad-v0.12.2-i386.deb
```
or
```
alien -r -c haroopad-v0.12.2-amd64.deb
```
Fourth, we install our brand new .rpm:
```
sudo zypper in haroopad-0.12.2-2.i386.rpm
```
or
```
sudo zypper in haroopad-0.12.2-2.amd64.rpm
```
Important: we accept to install it even if zypper complains for a missing dependency.

Fifth, we fix the missing library issue by creating a symlink to the equivalent library we have on openSUSE:
```
sudo ln -s /usr/lib/libudev.so.1 /usr/lib/libudev.so.0
```
That's it.

BTW, I wrote these notes on my freshly installed Haroopad :-)

descargar paquete 
```
libudev0-182-5.1.2.x86_64.rpm
```

## Virtualizacion

### Virtualizacion completa - KVM

### Virtualizacion ligera - LXC, Docket

adduser nombre_usuario kvm && adduser nombre_usuario libvirt

#Estructura general de los directorios Linux fuente

Fuente: http://blog.desdelinux.net/estructura-de-directorios-en-linux/

**En el sistema de ficheros de UNIX (y similares, como GNU/Linux), existen varias sub-jerarquías de directorios que poseen múltiples y diferentes funciones de almacenamiento y organización en todo el sistema. Estos directorios pueden clasificarse en:

**Estáticos: Contiene archivos que no cambian sin la intervención del administrador (root), sin embargo, pueden ser leídos por cualquier otro usuario. (/bin, /sbin, /opt, /boot, /usr/bin…)

**Dinámicos: Contiene archivos que son cambiantes, y pueden leerse y escribirse (algunos sólo por su respectivo usuario y el root). Contienen configuraciones, documentos, etc. (/var/mail, /var/spool, /var/run, /var/lock, /home…)

**Compartidos: Contiene archivos que se pueden encontrar en un ordenador y utilizarse en otro, o incluso compartirse entre usuarios.

**Restringidos: Contiene ficheros que no se pueden compartir, solo son modificables por el administrador. (/etc, /boot, /var/run, /var/lock…)

##Descripción de la estructura del árbol de directorios

##### / (raíz):
Parecido a el directorio raíz “C:\” de los sistemas operativos DOS y Windows. Es el nivel más alto dentro de la jerarquía de directorios, es el contenedor de todo el sistema (accesos al sistema de archivos, incluyendo los discos extraíbles [CD’s, DVD’s, pendrives, etc.]).

##### /bin (binarios):
Los binarios son los ejecutables de Linux (similar a los archivos .exe de Windows). Aquí tendremos los ejecutables de los programas propios del sistema operativo.

##### /boot (arranque):
Aquí nos encontramos los archivos necesarios para el inicio de Linux, desde los archivos de configuración del cargador de arranque (Grub – Lilo), hasta el propio kernel del sistema.

Cargador de arranque (boot loader en inglés): es un programa sencillo (que no tiene la totalidad de las funcionalidades de un sistema operativo) diseñado exclusivamente para preparar todo lo que necesita el sistema operativo para funcionar.

Núcleo o kernel: es un software que constituye la parte más importante del sistema operativo. Es el principal responsable de facilitar a los distintos programas acceso seguro al hardware de la computadora o en forma básica, es el encargado de gestionar recursos, a través de servicios de llamada al sistema.

##### /dev (dispositivos):
Esta carpeta contiene los dispositivos del sistema, incluso los que no se les ha asignado (montado) un directorio, por ejemplo micrófonos, impresoras, pendrives (memorias USB) y dispositivos especiales (por ejemplo, /dev/null). Linux trata los dispositivos como si fueran un fichero más para facilitar el flujo de la información.

/dev/null o null device (periférico nulo): es un archivo especial que descarta toda la información que se escribe o redirecciona en él. A su vez, no proporciona ningún dato a cualquier proceso que intente leer de él, devolviendo simplemente un EOF o fin de fichero. La forma más comúnmente utilizada es mediante la redirección, ya que /dev/null es un archivo especial y no un directorio; por lo tanto, no se pueden mover (mv) ni copiar (cp) ficheros en su interior.

##### /etc (etcétera):
Aquí se guardan los ficheros de configuración de los programas instalados, así como ciertos scripts que se ejecutan en el inicio del sistema. Los valores de estos ficheros de configuración pueden ser complementados o sustituidos por los ficheros de configuración de usuario que cada uno tiene en su respectivo “home” (carpeta personal).

##### /home (hogar):
Aquí se encuentran los ficheros de configuración de usuario así como los archivos personales del mismo (documentos, música, videos, etc.), a excepción del superusuario (administrador, root) el cual cuenta con un directorio aparte. Similar a “Mis Documentos” en Windows.

##### /media (media/medios):
Contiene los puntos de montaje de los medios extraíbles de almacenamiento, tales como lectores de CD-ROM , Pendrives (memoria USB), e incluso sirve para montar otras particiones del mismo disco duro, como por ejemplo, alguna partición que sea utilizada por otro sistema operativo.

##### /mnt (montajes):
Este directorio se utiliza normalmente para montajes temporales de unidades. Es una directorio semejante a /media, pero es usado mayoritariamente por los usuarios. Sirve para montar discos duros y particiones de forma temporal en el sistema; no necesita contraseña, a diferencia del directorio /media.

##### /opt (opcionales):
Contiene Paquetes de programas opcionales de aplicaciones estáticas, es decir, que pueden ser compartidas entre los usuarios. Dichas aplicaciones no guardan sus configuraciones en este directorio; de esta manera, cada usuario puede tener una configuración diferente de una misma aplicación, de manera que se comparte la aplicación pero no las configuraciones de los usuarios, las cuales se guardan en su respectivo directorio en /home.

##### /proc (procesos):
Contiene principalmente archivos de texto, sistema de archivos virtuales que documentan al núcleo y el estado de los procesos en archivos de texto (por ejemplo, uptime, network).

##### /root (administrador):
Es el /home del administrador (solo para él). Es el único /home que no está incluido -por defecto- en el directorio anteriormente mencionado.

##### /sbin (binarios de sistema):
Sistema de binarios especial, comandos y programas exclusivos del superusuario (root), por ejemplo, init, route, ifup, como mount, umount, shutdown). Un usuario puede ejecutar alguno de estas aplicaciones de comandos, si tiene los permisos suficientes, o bien, si tiene la contraseña del superusuario.

##### /srv (servicios):
Información del sistema sobre ciertos servicios que ofrece (FTP, HTTP…).

##### /tmp (temporales):
Es un directorio donde se almacenan ficheros temporales (por ejemplo: por el navegador de internet). Cada vez que se inicia el sistema este directorio se limpia.

##### /usr (usuarios):
Jerarquía secundaria de los datos de usuario; contiene la mayoría de las utilidades y aplicaciones multiusuario, es decir, accesibles para todos los usuarios. En otras palabras, contiene los archivos compartidos, pero que no obstante son de sólo lectura. Este directorio puede incluso ser compartido con otras computadoras de red local.

/var (variables): Archivos variables, tales como logs, archivos spool, bases de datos, archivos de e-mail temporales, y algunos archivos temporales en general. Generalmente actúa como un registro del sistema. Ayuda a encontrar los orígenes de un problema.

##### /sys (sistema):
Contiene parámetros de configuración del sistema que se está ejecutando. Datos referidos al kernel, bus, dispositivos, firmware, fs (filesystem) y otros.

##### /lost+found (perdido y encontrado):
En los sistemas Unix, cada una de las particiones/sistema de ficheros cuenta con un directorio llamado /lost+found en el cual se almacenan ficheros y directorios (o restos de ellos) recuperados tras una revisión del sistema de ficheros  a través de la herramienta fsck, todo ello provocado habitualmente por cuelgues del sistema, apagados forzados del equipo, cortes de corriente, etc.

###GRUB se carga y se ejecuta en 4 etapas:

1. La primera etapa del cargador la lee el BIOS desde el MBR.

2. La primera etapa carga el resto del gestor de arranque (segunda etapa). Si la segunda etapa está en una unidad grande, en ocasiones se carga una fase intermedia 1.5, que contiene código adicional para permitir que los cilindros por encima de 1024, o unidades tipo LBA, puedan leerse. El gestor de arranque 1.5 es almacenado (si es necesario) en el MBR o en la partición de arranque.

3. La segunda etapa del gestor de arranque ejecuta y muestra el menú de inicio de GRUB que permite al usuario elegir un sistema operativo y examinar y modificar los parámetros de inicio.

4. Después de elegir un sistema operativo, se carga y se le pasa el control.

GRUB soporta métodos de arranque directo, arranque chain-loading, LBA, ext2, ext3, ext4 y hasta "un pre-sistema operativo en máquinas x86 totalmente basado en comandos". Contiene tres interfaces: un menú de selección, un editor de configuración, y una consola de línea de comandos.


##### Estructura LVM
```
/boot
 LVM
	swap
    /root
    /home
    /usr
    /tmp
    /var
```
##Nota
Para opensuse el particionamiento de lvm se debe crear una partición sin formato, después se procede a crear el grupo LVM
```
https://activedoc.opensuse.org/book/opensuse-reference/chapter-3-advanced-disk-setup
https://en.opensuse.org/SDB:Partitioning
```
####vgdisplay
Información de los dispositivos. Espacio asignado y espacio disponible
####lvdisplay
####cat /proc/partitions
#Grub Linux
#Redimensionamiento de particiones

para verificar el tamaño de la partición utilizamos:

lvs

vgdisplay espacio libre

primero desmontar la partición

umount /tmp

Redimencionar particion


#Agregar nuevo disco a una máquina linux
Abrir virtmanager
seleccionar la maquina virtual a la que se quiere adicionar un disco duro

```
fdisk -l | more
```

Corrección de errores en caso de no detectar el disco con el tamaño adecuado debe cambiarse el bus del diso SCSI o IDE formato de almacenamiento qcow2.

vgdisplay

pvdisplay

primero crear particion fisica

```
cfdisk /dev/vdb -- disco adicionado
```
Crear partición, luego Write para escribir la partición y finalmente quit para salir

```
fdisk -l /dev/vdb
```
Una vez terminado el particionamiento se crea la partición física
```
pvcreate /dev/vdb
vgdisplay
```
Luego crear el Volumen lógico con:
```
vgcreate nombre_grupo /dev/vdb1
```

ejecutar:
```
lvs
```
 LV     VG       Attr     LSize   Pool Origin Data%  Move Log Copy%  Convert
  VLHOME SISTEMAS -wi-ao--   1,00g
  VLTMP  SISTEMAS -wi-ao--   1,00g
  VLUSR  SISTEMAS -wi-ao-- 952,00m

ejecutar:
```
lvcreate -L 500m -n volumen01 grupoA
```
resultado: Logical volume "volumen01" created

ejecutar:
```
lvs
```
LV        VG       Attr     LSize   Pool Origin Data%  Move Log Copy%  Convert
VLHOME    SISTEMAS -wi-ao--   1,00g
VLTMP     SISTEMAS -wi-ao--   1,00g
VLUSR     SISTEMAS -wi-ao-- 952,00m
volumen01 grupoA   -wi-a--- 500,00m


Luego ejecutar:
```
mkfs.ext3 -m 0 /dev/mapper/grupoA-volumen01
```

Resultado:

mke2fs 1.42.5 (29-Jul-2012)
Etiqueta del sistema de ficheros=
OS type: Linux
Tamaño del bloque=1024 (bitácora=0)
Tamaño del fragmento=1024 (bitácora=0)
Stride=0 blocks, Stripe width=0 blocks
128016 inodes, 512000 blocks
0 blocks (0.00%) reserved for the super user
Primer bloque de datos=1
Número máximo de bloques del sistema de ficheros=67633152
63 bloque de grupos
8192 bloques por grupo, 8192 fragmentos por grupo
2032 nodos-i por grupo
Respaldo del superbloque guardado en los bloques:
        8193, 24577, 40961, 57345, 73729, 204801, 221185, 401409

Allocating group tables: hecho
Escribiendo las tablas de nodos-i: hecho
Creating journal (8192 blocks): hecho
Escribiendo superbloques y la información contable del sistema de ficheros: hecho

montar la unidad creada

primero crear la carpeta donde deseamos montar la unidad

mkdir /mnt/volumen-01
mount /dev/mapper/grupoA-volumen01 /mnt/volumen-01/

#Montado automático de particiones
editar el archivo fstab y adicionar:
```
/dev/mapper/grupoA-volumen01 /mnt/volumen-01            ext3    defaults        0       2
```
Práctica
Crear grupoB de 1024M
crear volumen lógico vol-b01 de 700M
crear volumen lógico vol-b02 de 200M

#Ampliar el  tamaño del disco vitual
Ejecutamos el comando en el equipo Host con la máquina virtual apagada.
```
qemu-img resize lvm1.qcow2 +5G
```
Luego de ampliar el tamaño del disco duro ejecutamos:

```
Antes de ejecutar el comando el disco tenia un tamaño de 10.9 GB

root@debian1:~# fdisk -l /dev/sda

Disk /dev/sda: 15.9 GB, 15853420544 bytes
255 heads, 63 sectors/track, 1927 cylinders, total 30963712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a5e74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
* /dev/sda2          501758    20475903     9987073    5  Extended *
/dev/sda5          501760     1499135      498688   82  Linux swap / Solaris
/dev/sda6         1501184     5404671     1951744   83  Linux
/dev/sda7         5406720    20475903     7534592   8e  Linux LVM

root@debian1:~# cfdisk /dev/sda
```

Para particionar el disco de forma gráfica utilizamos * gparted.iso *

Adcionamos la iso a la maquina virtual iniciamos la máquina virtual.

Recordatorio
1.- redimensionar el disco duro virtual
2.- qemu-img resize ruta_disco +5G
3.- botear desde el CD-ROM (gparted.iso)
4.- Expandir la partición desde el entorno gráfico gparted.iso
5.- Reiniciar la máquina virtual
6.fdisk -l /dev/sda

root@debian1:~# fdisk -l /dev/sda

Disk /dev/sda: 15.9 GB, 15853420544 bytes
255 heads, 63 sectors/track, 1927 cylinders, total 30963712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a5e74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    30963711    15230977    5  Extended
/dev/sda5          501760     1499135      498688   82  Linux swap / Solaris
/dev/sda6         1501184     5404671     1951744   83  Linux
/dev/sda7         5406720    30963711    12778496   8e  Linux LVM

Practica aumentar el tamaño del disco virtual a 15G y crear un nuevo grupo LVM "servidores"

#Listar tarjetas de red del sistema
```
ls /sys/class/net/
```

#Para ver configuración tarjetas de red

```
/etc/network/interfaces
```

mostrar interfaces de red
```
root@debian1:~# ip addr show

root@debian1:~# ip addr show eth0
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 52:54:00:29:27:d6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.232/24 brd 192.168.122.255 scope global eth0
    inet6 fe80::5054:ff:fe29:27d6/64 scope link
       valid_lft forever preferred_lft forever

```
#ifconfig
```
cifconfig eth0
eth0      Link encap:Ethernet  HWaddr 52:54:00:29:27:d6
          inet addr:192.168.122.232  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fe29:27d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43061 (42.0 KiB)  TX bytes:57285 (55.9 KiB)
          Interrupt:11 Base address:0x8000
```
#Configuración manual eth0

#iface eth0 inet dhcp

iface eth0 inet static
address 192.168.122.100
netmask 255.255.255.0
gateway 192.168.122.1

#Configuración DNS

```
root@debian1:~# nano /etc/resolv.conf
nameserver 8.8.8.8
nameserver 200.87.100.10

```

#Puertos abiertos
```
root@debian1:~# netstat -natp
root@debian1:~# netstat -natp |grep 22

```

En el equipo HOST crear archivo hola.txt
comando para copiar archivos por ssh:
```
linux-68lz:/home/jorge/Documentos/DiplomadoLinux # scp hola.txt root@192.168.122.80:/tmp
```

comando para copiar carpetas por ssh:
```
linux-68lz:/home/jorge/Documentos/DiplomadoLinux # scp -r /tmp/datos_egpp/ root@192.168.122.80:/srv
```
#Nota nunca ingresar como root a una máquina remotamente

Crear carpeta:
```
root@debian1:/# mkdir -p /tmp/test/{aaa,bbb,ccc,dddd]}
```
Copiar la carpeta test al equipo Host
```
root@debian1:/# scp -r /tmp/test/ jorge@192.168.5.1:/home/jorge/
root@debian1:/# scp -r /tmp/test/ jorge@192.168.5.1:/home/jorge/
The authenticity of host '192.168.5.1 (192.168.5.1)' can't be established.
ECDSA key fingerprint is 53:55:0b:35:59:db:eb:95:0f:dd:96:0d:ef:2e:05:80.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.5.1' (ECDSA) to the list of known hosts.
Password:
```

# Ver usuarios conectados
Para ver los usuarios conectados al servidor ejecutamos el comando who
```
root@debian1:/# who
root     tty1         2015-05-27 07:28
jorge    pts/0        2015-05-27 07:29 (192.168.5.1)
jorge    pts/1        2015-05-27 07:44 (192.168.5.1)
jorge    pts/2        2015-05-27 07:45 (192.168.5.1)
jorge    pts/3        2015-05-27 07:45 (192.168.5.1)
jorge    pts/4        2015-05-27 07:45 (192.168.5.1)
```
#Crear una llave pública
ingresamos al home del usuario .ssh y creamos la clave:
```
jorge@linux-68lz:~/.ssh> ssh-keygen -t rsa -b 2048
Generating public/private rsa key pair.
Enter file in which to save the key (/home/jorge/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/jorge/.ssh/id_rsa.
Your public key has been saved in /home/jorge/.ssh/id_rsa.pub.
The key fingerprint is:
ac:84:f6:ad:2a:02:66:23:9c:b4:87:99:8b:bb:00:65 [MD5] jorge@linux-68lz.site
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|                 |
|  E              |
| +   . .         |
|+ * o . S        |
|+@ o o o         |
|B +   o .        |
|+..    .         |
|o+ ....          |
+--[MD5]----------+
jorge@linux-68lz:~/.ssh>
```
Luego ejecutamos:
```
jorge@linux-68lz:~/.ssh> ls -la
total 20
drwx------  2 jorge users 4096 may 27 07:50 .
drwxr-xr-x 38 jorge users 4096 may 27 07:48 ..
-rw-------  1 jorge users 1766 may 27 07:50 id_rsa -- llave privada, por seguridad nadie mas debe conocer este archivo
-rw-r--r--  1 jorge users  403 may 27 07:50 id_rsa.pub --- esta es la llave que debe copiarse.
-rw-r--r--  1 jorge users  715 may 26 20:09 known_hosts
```
Copiamos la llave publica al servidor:
```
jorge@linux-68lz:~/.ssh> ssh-copy-id -i /home/jorge/.ssh/id_rsa.pub root@192.168.5.100
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
root@192.168.5.100's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'root@192.168.5.100'"
and check to make sure that only the key(s) you wanted were added.
```
Para verificar la cabecera del archivo

head /root/.ssh .ssh

```
Para poder utilizar las llaves se debe modificar el archivo:
root@debian1:~# nano -c /etc/ssh/sshd_config
```
y modificar lo siguiente:
```
PubkeyAuthentication yes
```

#TRADUCIR

How it works

When ssh-agent is started, it will accept the input of new keys and provides these keys again trough a socket. This socket is only available for sub-processes of ssh-agent. This means ssh-agent must be invoked with another command as argument. This can be a shell or your complete X desktop. After ssh-agent is started, the program ssh-add can be used to add your private keys to the ssh-agent.
Basic invocation

In the following example ssh-agent is started from the command line, with bash as argument. This starts a bash session inside your current one, with ssh-agent in the background.
$ ssh-agent bash

Ssh-agent will keep running, until the sub shell bash is closed.
$ exit

This will terminate the bash session and ssh-agent.
Add your keys

You can use ssh-add to send your keys to the agent. Ssh-add only works if it can find the open socket. So it has to be executed in a sub shell of ssh-agent, like in the example above.
$ ssh-add

This command will look for the files ~/.ssh/id_rsa ~/.ssh/id_dsa ~/.ssh/identity and automatic add them. You will be prompted for your key's password if one is set. (That's usually the reason why one would choose to use ssh-agent.) The ssh-add command must be executed every time the ssh-agent is started.

davis.men.pa@gmail.com  LUNES 01/06/2015

#Permisos directorios consola

chown = cambiar el dueño de un archivo o directorio
```
chown jorge hola.txt
```
chown user:jorge reporte.txt = cambia el usuario dueño
reporte.txt de 'user' y el grupo propietario es jorge
-R = recursivo afecta todo el sub contenido del directorio
```
chown -R jorge:users /home/Daniel
```
chmod = modify user access/permission – simple way
u = user
g = group
o = other
d = directorio (si el elemento es un directorio)
l = link (si el elemento es un enlace)
r = read (permisos de lectura)
w = write (permisos de escritura)
x = eXecute (solo utilizado por for scripts y programas)

##Valor numérico
r lectura = 4
w escritura = 2
x ejecucion = 1

Ejercicio crear una carpeta prueba en el directorio tmp

ejecutar:

chmod  o+w prueba/

quitar permisos:

jorge@linux-68lz:/tmp> chmod  -rwx prueba/

d-------w- 2 jorge users 4,0K may 27 08:51 prueba

ejecutar:

jorge@linux-68lz:/tmp> chmod 437 prueba/
dr---wxrwx 2 jorge users 4,0K may 27 08:51 prueba

dr---wxrwx 2 jorge users 4,0K may 27 08:51 prueba

#Cambiar propietario de los directorio

linux-68lz:/tmp # chown -R root:users prueba/

#Crear, modificar cuentas de usuarios

sudo adduser jorge crea un nuevo usuario
sudo passwd <NombreCuenta> = cambia el password del usuario
sudo deluser <NombreCuenta> = elimina una cuenta
addgroup amigos = crea un nuevo grupo
delgroup amigos = elimina un grupo
usermod -g amigos <Cuenta> = adiciona el usuario al grupo
usermod -g jorge jorge1 = cambia el nombre de la cuenta


##Mostrar usuarios del sistema
```
linux-68lz:/tmp # getent passwd
```
o el equivalente
```
linux-68lz:/tmp # cat /etc/passwd
```
Resultado:
```
at:x:25:25:Batch jobs daemon:/var/spool/atjobs:/bin/bash
avahi:x:487:486:User for Avahi:/run/avahi-daemon:/bin/false
avahi-autoipd:x:499:499:User for Avahi IPv4LL:/var/lib/avahi-autoipd:/bin/false
bin:x:1:1:bin:/bin:/bin/bash
daemon:x:2:2:Daemon:/sbin:/bin/bash
dnsmasq:x:495:65534:dnsmasq:/var/lib/empty:/bin/false
ftp:x:40:49:FTP account:/srv/ftp:/bin/bash
games:x:12:100:Games account:/var/games:/bin/bash
icecream:x:481:477:Icecream Daemon:/var/cache/icecream:/bin/false
kdm:x:486:485:KDM Display Manager daemon:/var:/bin/false
lp:x:4:7:Printing daemon:/var/spool/lpd:/bin/bash
mail:x:8:12:Mailer daemon:/var/spool/clientmqueue:/bin/false
man:x:13:62:Manual pages viewer:/var/cache/man:/bin/bash
messagebus:x:498:496:User for D-Bus:/run/dbus:/bin/false
mysql:x:60:481:MySQL database admin:/var/lib/mysql:/bin/false
news:x:9:13:News system:/etc/news:/bin/bash
nobody:x:65534:65533:nobody:/var/lib/nobody:/bin/bash
nscd:x:497:494:User for nscd:/run/nscd:/sbin/nologin
ntp:x:74:495:NTP daemon:/var/lib/ntp:/bin/false
polkitd:x:494:492:User for polkitd:/var/lib/polkit:/sbin/nologin
postfix:x:51:51:Postfix Daemon:/var/spool/postfix:/bin/false
pulse:x:489:488:PulseAudio daemon:/var/lib/pulseaudio:/sbin/nologin
qemu:x:485:482:qemu user:/:/sbin/nologin
quagga:x:483:479:Quagga routing daemon:/run/quagga:/usr/bin/false
radvd:x:484:2:Router ADVertisement Daemon for:/var/lib/empty:/bin/false
root:x:0:0:root:/root:/bin/bash
rpc:x:490:65534:user for rpcbind:/var/lib/empty:/sbin/nologin
rtkit:x:492:490:RealtimeKit:/proc:/bin/false
scard:x:491:489:Smart Card Reader:/var/run/pcscd:/usr/sbin/nologin
sshd:x:493:491:SSH daemon:/var/lib/sshd:/bin/false
statd:x:488:65534:NFS statd daemon:/var/lib/nfs:/sbin/nologin
svn:x:482:478:user for Apache Subversion svnserve:/srv/svn:/sbin/nologin
tftp:x:496:493:TFTP account:/srv/tftpboot:/bin/false
uucp:x:10:14:Unix-to-Unix CoPy system:/etc/uucp:/bin/bash
wwwrun:x:30:8:WWW daemon apache:/var/lib/wwwrun:/bin/false
jorge:x:1000:100:Jorge Escobar Lopez:/home/jorge:/bin/bash
colord:x:480:475:user for colord:/var/lib/colord:/sbin/nologin
gdm:x:479:474:Gnome Display Manager daemon:/var/lib/gdm:/bin/false

```
```
linux-68lz:/tmp # sudo adduser usuario2
```
#Cambiar de usuario

```
linux-68lz:/tmp # su - jorge
```


