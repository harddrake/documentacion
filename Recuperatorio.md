#RECUPERATORIO DE PRACTICAS

DOCUMENTAR TODO EL PROCESO EN GITHUB CON CAPTURAS DE PANTALLA

1. CREAR DISCO DURO VIRTUAL 8 GB
2. CREAR GRUPO LVM SISTEMAS-kvm01
3. CREAS GRUPO LVM SISTEMAS-kvm02
4. CREAR 3 VOLUMENES LOGICOS DENTRO DE SISTEMAS-KVM

##Agregando disco virtual de 8 GB

Abrir Virt Manager

![](https://raw.githubusercontent.com/harddrake/documentacion/4f95fa1093539bd471a0a6fcd655f500a562644b/CrearDiscoVirtual8G-0.png)

En la barra de menú editar detalles de la conexión
Click en Nuevo Volumen
![](https://raw.githubusercontent.com/harddrake/documentacion/4f95fa1093539bd471a0a6fcd655f500a562644b/CrearDiscoVirtual8G-1.png)
Escribir el nombre del Nuevo Volumen
Seleccionamos formato del disco qcow2


Asignar el tamaño para el Volumen para este caso 8GB
luego click en Finalizar.

Abrimos la virtual y adcionamos el nuevo disco creado
selecionamos storage 
seleccionamos la opción "Elija administrado, o algún otro tipo de almacenamiento existente"
Presionamos el boton explorar y Seleccionamos el disco creado en este caso "discoPractica.qcow2"
Presionamos el Boton Finalizar
![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-3.png)

Encendemos la máquina virtual
iniciamos sesión

![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-5.png)
```
ejecutamos fdisk -l | more
```
Podemos ver el disco

![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-6.png)

```
ejecutamos cfdisk /dev/sdc
```

![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-7.png)

###Dividimos el disco en dos unidades para poder crear:

GRUPO LVM SISTEMAS-kvm01
GRUPO LVM SISTEMAS-kvm02
Se se crean dos particiones

![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-8.png)

creamos el volumen fisico pvcreate

 sdc1 
  ```
  root@debian1:~# pvcreate /dev/sdc1
  Writing physical volume data to disk "/dev/sdc1"
  Physical volume "/dev/sdc1" successfully created
```
![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-9.png)

 sdc2
```
root@debian1:~# pvcreate /dev/sdc2
  Writing physical volume data to disk "/dev/sdc2"
  Physical volume "/dev/sdc2" successfully created
```
![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-10.png)

creamos el grupo SISTEMAS-kvm01 en el disco /dev/sdc1
```
root@debian1:~# vgcreate SISTEMAS-kvm01 /dev/sdc1
  Volume group "SISTEMAS-kvm01" successfully created
```
creamos el grupo SISTEMAS-kvm02 en el disco /dev/sdc2
```
root@debian1:~# vgcreate SISTEMAS-kvm02 /dev/sdc2
  Volume group "SISTEMAS-kvm02" successfully created
  ```
![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-11.png)

Creamos 3 VOLUMENES lógicos en "SISTEMAS-kvm01" 
```
lvcreate -L 100m -n  grupo-kvm-1 SISTEMAS-kvm01
root@debian1:~# lvcreate -L 100m -n  grupo-kvm-1 SISTEMAS-kvm01
  Logical volume "grupo-kvm-1" created
```
```
lvcreate -L 200m -n  grupo-kvm-2 SISTEMAS-kvm01
root@debian1:~# lvcreate -L 200m -n  grupo-kvm-2 SISTEMAS-kvm01
  Logical volume "grupo-kvm-2" created
```
```
lvcreate -L 300m -n  grupo-kvm-3 SISTEMAS-kvm01 
root@debian1:~# lvcreate -L 300m -n  grupo-kvm-3 SISTEMAS-kvm01 
  Logical volume "grupo-kvm-3" created
  ```
Ejecutamos LVS
```
root@debian1:~# lvs
  LV          VG             Attr     LSize   Pool Origin Data%  Move Log Copy%  Convert
  VLHOME      SISTEMAS       -wi-ao-- 952,00m                                           
  VLTMP       SISTEMAS       -wi-ao-- 952,00m                                           
  VLUSR       SISTEMAS       -wi-ao-- 952,00m                                           
  grupo-kvm-1 SISTEMAS-kvm01 -wi-a--- 100,00m                                           
  grupo-kvm-2 SISTEMAS-kvm01 -wi-a--- 200,00m                                           
  grupo-kvm-3 SISTEMAS-kvm01 -wi-a--- 300,00m                                           
  vol100      egpp           -wi-ao-- 500,00m  
 ``` 
  ![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-16.png)

Creamos 3 VOLUMENES lógicos en "SISTEMAS-kvm02" 
```
lvcreate -L 100m -n  grupo2-kvm-1 SISTEMAS-kvm02
root@debian1:~# lvcreate -L 100m -n  grupo2-kvm-1 SISTEMAS-kvm02
  Logical volume "grupo2-kvm-1" created
```
```
lvcreate -L 100m -n  grupo2-kvm-2 SISTEMAS-kvm02
root@debian1:~# lvcreate -L 100m -n  grupo2-kvm-2 SISTEMAS-kvm02
  Logical volume "grupo2-kvm-2" created
```
```
lvcreate -L 100m -n  grupo2-kvm-3 SISTEMAS-kvm02
root@debian1:~# lvcreate -L 100m -n  grupo2-kvm-3 SISTEMAS-kvm02
  Logical volume "grupo2-kvm-3" created
```

Ejecutamos LVS
```
root@debian1:~# lvs
  LV           VG             Attr     LSize   Pool Origin Data%  Move Log Copy%  Convert
  VLHOME       SISTEMAS       -wi-ao-- 952,00m                                           
  VLTMP        SISTEMAS       -wi-ao-- 952,00m                                           
  VLUSR        SISTEMAS       -wi-ao-- 952,00m                                           
  grupo-kvm-1  SISTEMAS-kvm01 -wi-a--- 100,00m                                           
  grupo-kvm-2  SISTEMAS-kvm01 -wi-a--- 200,00m                                           
  grupo-kvm-3  SISTEMAS-kvm01 -wi-a--- 300,00m                                           
  grupo2-kvm-1 SISTEMAS-kvm02 -wi-a--- 100,00m                                           
  grupo2-kvm-2 SISTEMAS-kvm02 -wi-a--- 100,00m                                           
  grupo2-kvm-3 SISTEMAS-kvm02 -wi-a--- 100,00m                                           
  vol100       egpp           -wi-ao-- 500,00m                                           
```
  ![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-19.png)
Damos formato a los nuevos volumenes del grupo SISTEMAS-kvm01
```
root@debian1:~# mkfs.ext3 -m 0 /dev/mapper/SISTEMAS--kvm01-grupo--kvm--1
```
```
mke2fs 1.42.5 (29-Jul-2012)
Discarding device blocks: hecho                           
Etiqueta del sistema de ficheros=
OS type: Linux
Tamaño del bloque=1024 (bitácora=0)
Tamaño del fragmento=1024 (bitácora=0)
Stride=0 blocks, Stripe width=0 blocks
25688 inodes, 102400 blocks
0 blocks (0.00%) reserved for the super user
Primer bloque de datos=1
Número máximo de bloques del sistema de ficheros=67371008
13 bloque de grupos
8192 bloques por grupo, 8192 fragmentos por grupo
1976 nodos-i por grupo
Respaldo del superbloque guardado en los bloques: 
        8193, 24577, 40961, 57345, 73729

Allocating group tables: hecho                           
Escribiendo las tablas de nodos-i: hecho                           
Creating journal (4096 blocks): hecho
Escribiendo superbloques y la información contable del sistema de ficheros: hecho
```

![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-20.png)

```
root@debian1:~# mkfs.ext3 -m 0 /dev/mapper/SISTEMAS--kvm01-grupo--kvm--2 
mke2fs 1.42.5 (29-Jul-2012)
Discarding device blocks: hecho                           
Etiqueta del sistema de ficheros=
OS type: Linux
Tamaño del bloque=1024 (bitácora=0)
Tamaño del fragmento=1024 (bitácora=0)
Stride=0 blocks, Stripe width=0 blocks
51200 inodes, 204800 blocks
0 blocks (0.00%) reserved for the super user
Primer bloque de datos=1
Número máximo de bloques del sistema de ficheros=67371008
25 bloque de grupos
8192 bloques por grupo, 8192 fragmentos por grupo
2048 nodos-i por grupo
Respaldo del superbloque guardado en los bloques: 
        8193, 24577, 40961, 57345, 73729

Allocating group tables: hecho                           
Escribiendo las tablas de nodos-i: hecho                           
Creating journal (4096 blocks): hecho
Escribiendo superbloques y la información contable del sistema de ficheros: hecho
```
![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-21.png)
```
root@debian1:~# mkfs.ext3 -m 0 /dev/mapper/SISTEMAS--kvm01-grupo--kvm--3 
mke2fs 1.42.5 (29-Jul-2012)
Discarding device blocks: hecho                           
Etiqueta del sistema de ficheros=
OS type: Linux
Tamaño del bloque=1024 (bitácora=0)
Tamaño del fragmento=1024 (bitácora=0)
Stride=0 blocks, Stripe width=0 blocks
76912 inodes, 307200 blocks
0 blocks (0.00%) reserved for the super user
Primer bloque de datos=1
Número máximo de bloques del sistema de ficheros=67633152
38 bloque de grupos
8192 bloques por grupo, 8192 fragmentos por grupo
2024 nodos-i por grupo
Respaldo del superbloque guardado en los bloques: 
        8193, 24577, 40961, 57345, 73729, 204801, 221185

Allocating group tables: hecho                           
Escribiendo las tablas de nodos-i: hecho                           
Creating journal (8192 blocks): hecho
Escribiendo superbloques y la información contable del sistema de ficheros: hecho
```

Damos formato a los nuevos volumenes del grupo SISTEMAS-kvm02
```
root@debian1:~# mkfs.ext3 /dev/mapper/SISTEMAS--kvm02-grupo2--kvm--1
mke2fs 1.42.5 (29-Jul-2012)
Discarding device blocks: hecho                           
Etiqueta del sistema de ficheros=
OS type: Linux
Tamaño del bloque=1024 (bitácora=0)
Tamaño del fragmento=1024 (bitácora=0)
Stride=0 blocks, Stripe width=0 blocks
25688 inodes, 102400 blocks
5120 blocks (5.00%) reserved for the super user
Primer bloque de datos=1
Número máximo de bloques del sistema de ficheros=67371008
13 bloque de grupos
8192 bloques por grupo, 8192 fragmentos por grupo
1976 nodos-i por grupo
Respaldo del superbloque guardado en los bloques: 
        8193, 24577, 40961, 57345, 73729

Allocating group tables: hecho                           
Escribiendo las tablas de nodos-i: hecho                           
Creating journal (4096 blocks): hecho
Escribiendo superbloques y la información contable del sistema de ficheros: hecho
```

```
root@debian1:~# mkfs.ext3 /dev/mapper/SISTEMAS--kvm02-grupo2--kvm--2
mke2fs 1.42.5 (29-Jul-2012)
Discarding device blocks: hecho                           
Etiqueta del sistema de ficheros=
OS type: Linux
Tamaño del bloque=1024 (bitácora=0)
Tamaño del fragmento=1024 (bitácora=0)
Stride=0 blocks, Stripe width=0 blocks
25688 inodes, 102400 blocks
5120 blocks (5.00%) reserved for the super user
Primer bloque de datos=1
Número máximo de bloques del sistema de ficheros=67371008
13 bloque de grupos
8192 bloques por grupo, 8192 fragmentos por grupo
1976 nodos-i por grupo
Respaldo del superbloque guardado en los bloques: 
        8193, 24577, 40961, 57345, 73729

Allocating group tables: hecho                           
Escribiendo las tablas de nodos-i: hecho                           
Creating journal (4096 blocks): hecho
Escribiendo superbloques y la información contable del sistema de ficheros: hecho
```

```
root@debian1:~# mkfs.ext3 /dev/mapper/SISTEMAS--kvm02-grupo2--kvm--3
mke2fs 1.42.5 (29-Jul-2012)
Discarding device blocks: hecho                           
Etiqueta del sistema de ficheros=
OS type: Linux
Tamaño del bloque=1024 (bitácora=0)
Tamaño del fragmento=1024 (bitácora=0)
Stride=0 blocks, Stripe width=0 blocks
25688 inodes, 102400 blocks
5120 blocks (5.00%) reserved for the super user
Primer bloque de datos=1
Número máximo de bloques del sistema de ficheros=67371008
13 bloque de grupos
8192 bloques por grupo, 8192 fragmentos por grupo
1976 nodos-i por grupo
Respaldo del superbloque guardado en los bloques: 
        8193, 24577, 40961, 57345, 73729

Allocating group tables: hecho                           
Escribiendo las tablas de nodos-i: hecho                           
Creating journal (4096 blocks): hecho
Escribiendo superbloques y la información contable del sistema de ficheros: hecho
```

Finalmente creamos los directorios para montar las nuevas unidades
```
  grupo-kvm-1  SISTEMAS-kvm01 -wi-a--- 100,00m                                           
  grupo-kvm-2  SISTEMAS-kvm01 -wi-a--- 200,00m                                           
  grupo-kvm-3  SISTEMAS-kvm01 -wi-a--- 300,00m                                           
  grupo2-kvm-1 SISTEMAS-kvm02 -wi-a--- 100,00m                                           
  grupo2-kvm-2 SISTEMAS-kvm02 -wi-a--- 100,00m                                           
  grupo2-kvm-3 SISTEMAS-kvm02 -wi-a--- 100,00m                                           
```
```
root@debian1:~# mkdir -p /mnt/practica/{grupo-kvm-1,grupo-kvm-2,grupo-kvm-3,grupo2-kvm-1,grupo2-kvm-2,grupo2-kvm-3}
```
Montamos las unidades en sus respectivos directorios
```
root@debian1:/# mount /dev/mapper/SISTEMAS--kvm01-grupo--kvm--1 /mnt/practica/grupo-kvm-1/

root@debian1:/# mount /dev/mapper/SISTEMAS--kvm01-grupo--kvm--2 /mnt/practica/grupo-kvm-2/

root@debian1:/# mount /dev/mapper/SISTEMAS--kvm01-grupo--kvm--3 /mnt/practica/grupo-kvm-3/

root@debian1:/# mount /dev/mapper/SISTEMAS--kvm02-grupo2--kvm--1 /mnt/practica/grupo2-kvm-1/

root@debian1:/# mount /dev/mapper/SISTEMAS--kvm02-grupo2--kvm--2 /mnt/practica/grupo2-kvm-2/

root@debian1:/# mount /dev/mapper/SISTEMAS--kvm02-grupo2--kvm--3 /mnt/practica/grupo2-kvm-3/
```
Ejecutamos df -h 
```
root@debian1:/# df -h
S.ficheros                                             Tamaño Usados  Disp Uso% Montado en
rootfs                                                   1,9G   279M  1,5G  16% /
udev                                                      10M      0   10M   0% /dev
tmpfs                                                    101M   284K  101M   1% /run
/dev/disk/by-uuid/dddc6a9b-3fc8-4e30-beda-b331c3b0573f   1,9G   279M  1,5G  16% /
tmpfs                                                    5,0M      0  5,0M   0% /run/lock
tmpfs                                                    298M      0  298M   0% /run/shm
/dev/sdb1                                                228M    18M  199M   9% /boot
/dev/mapper/SISTEMAS-VLHOME                              938M    18M  873M   2% /home
/dev/mapper/SISTEMAS-VLTMP                               938M    18M  873M   2% /tmp
/dev/mapper/SISTEMAS-VLUSR                               938M   348M  543M  40% /usr
/dev/mapper/egpp-vol100                                  485M    11M  449M   3% /mnt/examen
/dev/mapper/SISTEMAS--kvm01-grupo--kvm--1                 97M   5,6M   92M   6% /mnt/practica/grupo-kvm-1
/dev/mapper/SISTEMAS--kvm01-grupo--kvm--2                194M   5,6M  189M   3% /mnt/practica/grupo-kvm-2
/dev/mapper/SISTEMAS--kvm01-grupo--kvm--3                291M    11M  281M   4% /mnt/practica/grupo-kvm-3
/dev/mapper/SISTEMAS--kvm02-grupo2--kvm--1                97M   5,6M   87M   7% /mnt/practica/grupo2-kvm-1
/dev/mapper/SISTEMAS--kvm02-grupo2--kvm--2                97M   5,6M   87M   7% /mnt/practica/grupo2-kvm-2
/dev/mapper/SISTEMAS--kvm02-grupo2--kvm--3                97M   5,6M   87M   7% /mnt/practica/grupo2-kvm-3
```
![](https://raw.githubusercontent.com/harddrake/documentacion/14adbb4bb84fe9d8a7423f5cc9a714b71178e88e/CrearDiscoVirtual8G-26.png)
