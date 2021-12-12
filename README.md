## NuTyX

**SPANISH** [NuTyX](http://www.nutyx.org) es una distribución GNU/Linux para multiples arquitecturas inspirada en la documentación online de [Linux From Scratch (LFS)](http://www.linuxfromscratch.org).

NuTyX cuenta con un gestor de paquetes personalizado llamado "cards". Cards puede instalar paquetes binarios, un conjunto de paquetes binarios (ej. KDE, Xfce), y compilar paquetes desde la fuente utilizando "ports". La distribución esta diseñada para usuarios de Linux intermedios y avanzados.

Documentación (en): http://nutyx.org/en/documentation

---

## NuTyX (Xposed)
**SPANISH** NuTyX Xposed provee paquetes extras, más actualizados y estables en comparación con la versión "testing" y "rolling".

### Instalación (usuarios experimentados) - RECOMENDADA
Para iniciar la instalación el liveiso o el S.O anfitrión debe contar con:
* curl
* libarchive (bsdtar) - Ubuntu 18.10 o superior no cuenta con bsdtar

*->Descargar NuTyX-Xposed Liveiso: http://nutyx-xposed.ddns.net/download*

**Pasos:**

***1.*** Bootear liveiso del sistema anfitrion. *Recomendado: [Descargar Nutyx-Xposed Liveiso.](http://nutyx.org/en/?page=base-commands#5)*

***2.*** Formatear y preparar las particiones para la instalación

***2.*** Montar particiones, utilizando **/mnt/hd** como root (/)

***3.*** Utilizar *bash* como intérprete de comandos (# /bin/bash)

#### Desde NuTyX-Xposed Liveiso:

***4.*** STAGE=base install-nutyx -t

#### Desde otras distribuciones Linux:

***4.*** curl -O http://nutyx-xposed.ddns.net/install-nutyx

***4-1.*** chmod +x install-nutyx

***4-2.*** STAGE=base ./install-nutyx -t

Mostrará una lista de variables y opciones disponibles.

Posibles opciones para la variable **STAGE**:

STRICT, BASE, CLI, GUI, GUI_EXTRA, XORG, GNOME, GNOME_EXTRA, KDE5, KDE5_EXTRA, OPENBOX, JWM, I3, LXDE, XFCE4, MATE. 
Cada variable indica el conjunto de paquetes que se instalarán siguendo el siguiente orden jerarquico.

**STRICT** ->   STRICT

**MINI** ->     STRICT + MINI

**BASE** ->     STRICT + BASE

**CLI** ->      STRICT + BASE + CLI

**GUI** ->      STRICT + BASE + CLI + GUI

**XORG** ->     STRICT + BASE + CLI + GUI + XORG

**JWM** ->      STRICT + BASE + CLI + GUI + GUI_EXTRA + XORG + JWM

**I3** ->       STRICT + BASE + CLI + GUI + GUI_EXTRA + XORG + I3

**OPENBOX** ->  STRICT + BASE + CLI + GUI + GUI_EXTRA + XORG + OPENBOX

**LXDE** ->     STRICT + BASE + CLI + GUI + GUI_EXTRA + XORG + LXDE

**XFCE4** ->    STRICT + BASE + CLI + GUI + GUI_EXTRA + XORG + XFCE4

**MATE** ->     STRICT + BASE + CLI + GUI + GUI_EXTRA + XORG + MATE

**GNOME** ->    STRICT + BASE + CLI + GUI + GUI_EXTRA + XORG + GNOME + GNOME_EXTRA

**KDE5** ->     STRICT + BASE + CLI + GUI + GUI_EXTRA + XORG + KDE5 + KDE5_EXTRA 

Es decir que al definir STAGE=XORG se instalarán los paquetes del conjunto STRICT + BASE + CLI + GUI + XORG
Una vez aclarado esto podemos proseguir con la instalación.

***5.*** sudo ISO=XORG ./install-nutyx

Finalizada la instalación podemos utilizar el gestor de arranque de una instalación previa existente o instalar/configurar grub en la nueva instalación de NuTyX mediante **chroot**:

***6.*** ./install-nutyx -ec

*Podria servirte: [Gestionar paquetes con cards.](http://nutyx.org/en/?page=base-commands#5)*

*Podria servirte: [Configurando GRUB en NuTyX.](http://nutyx.org/en/grub-install)*

*Podria servirte: [Configurar GRUB.](https://wiki.archlinux.org/title/GRUB)*


***7.*** Generar fstab *(opcional)* [Genfstab.](https://git.ckyln.com/genfstab/file/README.html)

Por defecto, NuTyX Xposed utiliza [SysVinit](http://nutyx.org/en/sysvinit) pero es compatible con Systemd y Runyx.

---

### Instalación para nuevos usuarios

***1.*** Descargar y bootear [NuTyX.iso](http://nutyx.org/en/downloads#2)

***2.*** Iniciar instalación

***3.*** Reiniciar sistema y configurar datos post-instalación

***4.*** Configurar las variables "version" y "url" dentro de /etc/cards.conf

	version xposed

	url http://nutyx-xposed.ddns.net

***5.*** cards sync

***6.*** cards upgrade