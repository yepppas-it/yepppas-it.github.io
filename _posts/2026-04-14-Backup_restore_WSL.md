---
title: Backup/Restore de instancias de WSL
categories: [Virtualización,WSL]
tags: [windows,WSL,Backup,Restore]     # TAG names should always be lowercase
---

Realizar un respaldo y restauración de una instancia de WSL (Windows Subsystem for Linux) es un proceso directo que se hace desde la terminal de Windows (PowerShell o CMD) utilizando los comandos de exportación e importación.

# Backup

## Realizar el Backup

Este proceso crea un archivo comprimido (`.tar`) que contiene todo el sistema de archivos de tu distribución.

**Identificar la instancia**: Abrir **PowerShell** y listar las distribuciones instaladas para copiar el nombre exacto.

```bash
wsl --list --verbose
```
```bash
C:\WSL> wsl --list
Distribuciones de subsistema de Windows para Linux:
Ubuntu-24.04 (Predeterminado)
docker-desktop
kali-linux
Debian
```
**Cerrar la instancia**: Es recomendable apagar WSL para asegurar que no haya archivos en uso.

```bash
wsl --shutdown
```
Exportar la distribución: Usaremos el comando `--export` indicando el nombre de la distro y la ruta donde quieres guardar el backup.

```bash
wsl --export <NombreDistro> <RutaArchivo.tar>
```
```bash
wsl --export Debian Backup-debian.tar
```
```bash
C:\WSL> wsl --export Debian Backup-debian.tar
Exportación en curso. Esta operación puede tardar unos minutos.
La operación se completó correctamente.
```

# Restore

## Realizar el restore

Se puede restaurar el backup en la misma computadora (como una distro nueva) o en otra diferente.

**Crear una carpeta de destino**: Decidir dónde se guardarán los archivos de la «nueva» instancia (donde se descomprimirá el VHDX).

**Importa el backup**: Usa el comando `--import` definiendo un nombre para la instancia, la carpeta de instalación y la ruta del archivo `.tar`.

```bash
wsl --import <NuevoNombre> <CarpetaInstalacion> <RutaArchivo.tar>
```
```bash
wsl --import Debian C:\Personal\WSL\Debian Backup-debian.tar
```
```bash
C:\Personal\WSL>wsl --import Debian C:\Personal\WSL\Debian Backup-debian.tar
La operación se completó correctamente.
```

# Configuración WSL
## Consideración importante del usuario por defecto

Al restaurar una instancia, WSL suele iniciar sesión como root por defecto. 

Para volver a usar tu usuario original automáticamente, debes crear o editar el archivo `/etc/wsl.conf` dentro de la instancia restaurada:

1. Entra a la instancia:

```bash
wsl -d Debian
```
2. Editar el archivo:

```bash
sudo nano /etc/wsl.conf
```

3. Añadir estas líneas

```bash
[user]
default = tu_nombre_de_usuario
```

4. Reinicia la instancia en PowerShell.

```bash
wsl --terminate Debian
```