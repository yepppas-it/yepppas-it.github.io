---
title: Instalación y configuración de Alpine Linux
categories: [Sistema operativo, Alpine Linux]
tags: [linux,alpine,install]     # TAG names should always be lowercase
---

La instalación de Alpine Linux, es un proceso un tanto diferente al de otras distribuciones «amigables».

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> En este artículo nos centraremos en la instalación de Alpine Linux sobre una máquina virtual.
{: .prompt-info }
<!-- markdownlint-restore -->

# Descarga de la ISO

La descarga de la ISO, se puede realizar accediendo a la siguiente página: <https://www.alpinelinux.org/downloads/>

Se dispone de varias opciones de descarga, pero dado que se implementará sobre una máquina virtual, utilizaremos la versión **VIRTUAL**.

![Download](assets/posts/2026-04-14/2026-04-14_01.png){: .normal}


# Instalación del sistema operativo

Una vez descargada la imagen y mapeada en la máquina virtual, se procederá a iniciar.

Cuando arranque, llegará a un punto donde nos solicitará el login de localhost.

```bash
OpenRC 0.63 is starting up Linux 6.18.7-0-virt (x86_64)

 * /proc is already mounted
 * Mounting /run ...                                                         [ ok ]
 * /run/openrc: creating directory
 * /run/lock: creating directory
 * /run/lock: correcting owner
 * Caching service dependencies ...                                          [ ok ]
 * Remounting devtmpfs on /dev ...                                           [ ok ]
 * Mounting /dev/mqueue ...                                                  [ ok ]
 * Mounting modloop ...                                                      [ ok ]
 * Verifying modloop ...                                                     [ ok ]
 * Mounting security filesystem ...                                          [ ok ]
 * Mounting debug filesystem ...                                             [ ok ]
 * Mounting trace filesystem ...                                             [ ok ]
 * Mounting persistent storage (pstore) filesystem ...                       [ ok ]
 * Mounting bpf filesystem ...                                               [ ok ]
 * Starting busybox mdev ...                                                 [ ok ]
 * Scanning hardware for mdev ...                                            [ ok ]
 * Loading hardware drivers ...                                              [ ok ]
 * Loading modules ...                                                       [ ok ]
 * Setting system clock using the hardware clock [UTC] ...                   [ ok ]
 * Checking local filesystems ...                                            [ ok ]
 * Remounting filesystems ...                                                [ ok ]
 * Mounting local filesystems ...                                            [ ok ]
 * Configuring kernel parameters ...                                         [ ok ]
 * Creating user login records ...                                           [ ok ]
 * Cleaning /tmp directory ...                                               [ ok ]
 * Setting hostname to localhost from /etc/hostname ...                      [ ok ]
 * Starting busybox syslog ...                                               [ ok ]
 * Starting firstboot ...                                                    [ ok ]

Welcome to Alpine Linux 3.23
Kernel 6.18.7-0-virt on x86_64 (/dev/tty1)

localhost login: _
```

Nos logearemos como **root**.

Una vez autenticado, ejecutaremos el siguiente comando.

```bash
setup-apline
```

```bash
localhost:~# setup-alpine

ALPINE LINUX INSTALL
--------------------

Keymap
------
af   al   am   ara  at   az   ba   bd   be   bg   br   brai by   ca   ch   cm   cn   cz   de   dk   dz   ee   epo  es   fi   fo
fr   gb   ge   gh   gr   hr   hu   id   ie   il   in   iq   ir   is   it   jp   ke   kg   kr   kz   la   latam lk   lt   lu   ma
md   me   mk   ml   mm   mt   my   ng   nl   no   nz   ph   pk   pl   pt   ro   rs   ru   se   si   sk   sy   th   tj   tm   tr
tu   ua   us   uz   vn

Select keyboard layout: [none] _
```