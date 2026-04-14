---
title: Instalación de Podman en Alpine Linux
categories: [Podman]
tags: [linux,alpine,podman,install]     # TAG names should always be lowercase
---

# Podman

Podman (Pod Manager) es un motor de contenedores completo y una herramienta sencilla y sin demonio.

## [Instalación de Podman](https://wiki.alpinelinux.org/wiki/Podman)

Podman se puede instalar a través del paquete podman en el repositorio de la comunidad, mediante el siguiente comando.

```bash
apk add podman
```

## Configuración de Podman

Para ejecutar podman con todas las funciones, es necesario habilitar el servicio **cgroups** en modo **v2** o **unificado** , que es el valor predeterminado actual. 

Para ello, ejecutaremos los siguientes comandos:

```bash
rc-update add cgroups
```
```bash
rc-service cgroups start
```

La configuración predeterminada del controlador de almacenamiento en `/etc/containers/storage.conf` es **overlay**.

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> Es posible que necesite reiniciar su máquina en esta etapa para que los cambios anteriores funcionen correctamente.
{: .prompt-warning }
<!-- markdownlint-restore -->