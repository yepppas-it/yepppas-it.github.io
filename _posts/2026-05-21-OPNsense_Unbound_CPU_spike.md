---
title: OPNsense - CPU alta por Unbound
categories: [Networking,OPNsense]
tags: [OPNsense,Unbound DNS,Python, DB, Fix]     # TAG names should always be lowercase
---

# Escenario

En una revisión rutinaria en el equipo **OPNsense**, se accede al panel de **Reporting** → **Unbound DNS**, y se comprueba que no hay datos registrados.
Al volver al panel de **Lobby** (panel principal), se comprueba que el Widget de CPU muestra un incremento de CPU que llega al 100%. Este uso de CPU se sostiene en el tiempo, provocando un incremento en la temperatura del equipo. Algo no esta funcionando correctamente, y se procede a investigar.

# Investigación

Con el fin de obtener más detalles sobre el fallo, se accede al *shell* del sistema.

Se ejecuta un `top`, para ver el estado de procesos del sistema.

```shell
$ top

last pid:  5626;  load averages:  1.69,  1.53,  0.78                                                                                                                                       up 0+00:06:04  12:15:34
90 processes:  2 running, 88 sleeping
CPU: 34.4% user,  0.0% nice,  4.7% system,  0.0% interrupt, 60.9% idle
Mem: 2100M Active, 1068M Inact, 1407M Wired, 56K Buf, 7128M Free
ARC: 447M Total, 103M MFU, 272M MRU, 30M Anon, 3334K Header, 39M Other
     324M Compressed, 935M Uncompressed, 2.88:1 Ratio
Swap: 8192M Total, 8192M Free

  PID USERNAME    THR PRI NICE   SIZE    RES STATE    C   TIME    WCPU COMMAND
97880 root          8 135    0    19G   112M CPU0     0   1:56  99.03% python3.13
 2863 root          1  20    0    60M    33M accept   1   0:02   3.44% php-cgi
48598 root          3  68    0    78M    39M accept   2   0:01   2.46% python3.13
 3564 root          1  20    0    60M    32M accept   0   0:02   2.01% php-cgi
 ...
 ```

Se dedice identificar y listar todos los archivos que tiene abiertos el proceso de **python3.13** que utiliza más CPU.

```shell
$ fstat -p 97880
USER     CMD          PID   FD MOUNT      INUM MODE         SZ|DV R/W
root     python3.13 97880 text /        200144 -r-xr-xr-x    4880  r
root     python3.13 97880   wd /         88586 drwxr-xr-x      24  r
root     python3.13 97880 root /            34 drwxr-xr-x      28  r
root     python3.13 97880    0 /dev         20 crw-rw-rw-    null rw
root     python3.13 97880    1 /dev         20 crw-rw-rw-    null rw
root     python3.13 97880    2* pipe fffffe00d2a16718 <-> fffffe00d2a165c0      0 rw
root     python3.13 97880    3 /        210488 -rwxr-xr-x    2517  r
root     python3.13 97880    4 /           604 -rw-r-----  105916 rw
root     python3.13 97880    5 /         97278 -rw-r-----  2895872  w
root     python3.13 97880    6 /         97278 -rw-r-----  2895872  w
root     python3.13 97880    7 /         97278 -rw-r-----  2895872  w
root     python3.13 97880    8 /         97278 -rw-r-----  2895872  w
root     python3.13 97880    9 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   10 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   11 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   12 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   13 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   14 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   15 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   16 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   17 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   18 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   19 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   20 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   21 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   22 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   23 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   24 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   25 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   26 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   27 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   28 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   29 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   30 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   31 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   32 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   33 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   34 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   35 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   36 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   37 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   38 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   39 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   40 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   41 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   42 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   43 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   44 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   45 /         97278 -rw-r-----  2895872  w
root     python3.13 97880   46 /         97278 -rw-r-----  2895872  w
...
```

Se observa que el proceso tiene abiertas decenas de conexiones simultáneas contra el mismo inodo.
Buscamos la correspondencia del inodo al archivo asociado.

```shell
$ find / -inum 97278
/var/unbound/data/unbound.duckdb
```

Se consulta información sobre este archivo. Se trata de una base de datos relacional ultrarrápida llamada **DuckDB**, que se utiliza para almacenar localmente las estadísticas de las peticiones DNS, los dominios bloqueados (bloqueo de publicidad/malware) y la telemetría que luego ves en los gráficos muy bonitos de la interfaz web.

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> El archivo `.duckdb` es una base de datos en un solo archivo. Al sufrir un corte de luz o un reinicio agresivo del entorno de virtualización, el índice interno de la base de datos se ha corrompido. El script de telemetría de Python entra en un bucle infinito intentando escribir los nuevos datos de navegación de tu red en una base de datos corrupta que los rechaza, provocando la fuga de descriptores de archivo que vimos en el `fstat`.
{: .prompt-info }
<!-- markdownlint-restore -->


# Resolución

Se detiene el servicio de Unbound temporalmente para que libere cualquier bloqueo:

```shell
pluginctl dns stop
```

Matamos el proceso zombi de Python para liberar la CPU (asegúrate de buscar su PID actual con top o usa el comando killall para fulminar cualquier script de telemetría de Unbound colgado):

```shell
killall -9 python3.13
```

Elimina la base de datos corrupta (el archivo que encontramos):

```shell
rm -f /var/unbound/data/unbound.duckdb
```

Vuelvemos a iniciar el servicio DNS:

```shell
pluginctl dns start
```

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> Al arrancar, Unbound verá que no existe unbound.duckdb, creará un archivo nuevo totalmente limpio de 0 bytes y Python podrá escribir en él instantáneamente sin esfuerzo, bajando el consumo de CPU.
{: .prompt-tip }
<!-- markdownlint-restore -->

