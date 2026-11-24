---
title: Atajos de teclado y acceso rápido en Windows
categories: [Sistema operativo,Windows]
tags: [windows,shortcut]     # TAG names should always be lowercase
---

Referencia rápida sobre navegación y gestión ágil en Windows.

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> En este artículo se recopilan atajos de teclado clave para agilizar el entorno de trabajo y comandos de ejecución directa (<kbd>Win</kbd> + <kbd>R</kbd>) indispensables para lanzar consolas y herramientas de diagnóstico al instante.
{: .prompt-info }
<!-- markdownlint-restore -->


## Comandos de ejecución directa

Existen decenas de comandos de ejecución directa que puedes lanzar desde el cuadro Ejecutar (Win + R), el menú Inicio o la terminal sin escribir su extensión.

### Consolas de administración (`.msc`)

Son complementos que se cargan directamente dentro de la interfaz de mmc.exe:
- `devmgmt.msc`: Administrador de dispositivos.
- `diskmgmt.msc`: Administración de discos (particiones y unidades).
- `services.msc`: Servicios locales del sistema.
- `eventvwr.msc`: Visor de eventos (logs de sistema, seguridad y aplicaciones).
- `gpedit.msc`: Editor de directivas de grupo local (solo en ediciones Pro, Enterprise y Education).
- `secpol.msc`: Directiva de seguridad local.
- `lusrmgr.msc`: Usuarios y grupos locales.
- `compmgmt.msc`: Administración de equipos (agrupa varias de las consolas anteriores en una sola ventana).
- `taskschd.msc`: Programador de tareas.
- `perfmon.msc`: Monitor de rendimiento.
- `certmgr.msc`: Administrador de certificados del usuario actual (certlm.msc para el equipo local).

### Diagnóstico, red y sistema (`.exe`)

- `msinfo32`: Información detallada del hardware y software del sistema.
- `dxdiag`: Herramienta de diagnóstico de DirectX (útil para revisar GPU, sonido y controladores).
- `resmon`: Monitor de recursos (uso detallado de CPU, memoria, disco y red).
- `perfmon` /`rel`: Monitor de confiabilidad (historial visual de errores críticos y actualizaciones).
- `regedit`: Editor del Registro de Windows.
- `msconfig`: Configuración del sistema (arranque y servicios).
- `taskmgr`: Administrador de tareas.
- `mstsc`: Conexión a Escritorio remoto (RDP).
- `cmd` / `wt` / `powershell`: Símbolo del sistema, Windows Terminal o PowerShell.
- `cleanmgr`: Liberador de espacio en disco.
- `mdsched`: Diagnóstico de memoria de Windows (requiere reinicio).

### Paneles de configuración rápida (`.cpl`)

Abren directamente las pestañas clásicas del Panel de control:

- `ncpa.cpl`: Conexiones de red (adaptadores Ethernet/Wi-Fi).
- `appwiz.cpl`: Programas y características (desinstalar software).
- `sysdm.cpl`: Propiedades del sistema (nombre del equipo, dominio, variables de entorno y rendimiento).
- `inetcpl.cpl`: Propiedades de Internet (proxy y certificados).
- `firewall.cpl`: Firewall de Windows Defender.
- `powercfg.cpl`: Opciones de energía.
- `control`: Panel de control general.


## [Atajos de teclado](https://support.microsoft.com/es-es/accessibility/windows/keyboard-shortcuts-in-windows)

### Atajos de teclado con la tecla Windows

Al combinar la tecla Windows con otras teclas, puede realizar rápidamente tareas comunes.

- <kbd>Win</kbd> + <kbd>v</kbd> → Abre el historial del portapapeles.
