---
title: Atajos de teclado para Kate
categories: [General,Editor de texto,Kate]
tags: [kate,shortcut]     # TAG names should always be lowercase
---

Kate es un editor de texto avanzado, gratuito y de código abierto, que ofrece numerosas herramientas para facilitar la edición de texto y código. 
Además de las funciones habituales de un editor, incorpora características que permiten agilizar tareas repetitivas, trabajar con múltiples documentos y personalizar el entorno de trabajo.

Una de las características más interesantes de Kate es la gran cantidad de [atajos de teclado](https://docs.kde.org/stable_kf6/en/kate/katepart/keybindings.html) que incorpora. En este artículo, voy a listar algunas de las que considero más útiles.

## Atajos de teclado

Se detallan según tipo de acción, los atajos de teclado.

### Comentar una línea o bloque de líneas

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> Para comentar/descomentar la línea actual o un bloque de texto seleccionado, aplicando el símbolo de comentario correcto de forma automática.
{: .prompt-info }
<!-- markdownlint-restore -->

- <kbd>Ctrl</kbd> + <kbd>d</kbd> → Añade automáticamente el símbolo de comentario correcto según el lenguaje o resaltado de sintaxis del archivo.
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>d</kbd> → Quita el comentario correcto según el lenguaje o resaltado de sintaxis del archivo.

### Mover una línea 



## Procedimientos

Se detallan procedimientos que requieren el uso de diferentes combinaciones teclas.

### Edición multicursor: modificar varias líneas simultáneamente

La edición multicursor, permite modificar múltiples líneas a la vez. 

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
> Esto es muy útil cuando deseamos comentar una parte o todo el texto de un código o configuración.
{: .prompt-tip }
<!-- markdownlint-restore -->

1. Pulsa <kbd>Ctrl</kbd> + <kbd>A</kbd>, para seleccionar todo el texto.
2. Pulsa <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>I</kbd>. Esto creará un cursor en cada línea de selección.
3. Pulsa <kbd>Inicio</kbd>, para mover todos los cursores al principio de cada línea.
4. Escribiremos el caracter deseado a insertar. En nuestro caso el caracter `#` para comentar todas las líneas de un archivo.
5. Pulsaremos <kbd>Esc</kbd> cuando se termine para volver a un solo cursor.

