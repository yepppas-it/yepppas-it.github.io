---
title: Personalizar configuración de VIM
categories: [General,Editor de texto,VIM]
tags: [VIM,Markdown]     # TAG names should always be lowercase
---

# Configuración básica para archivos Markdown

Se creará el archivo `~/.vimrc`, y se establecerá lo siguiente:

```vim
" ============================================================================
" CONFIGURACIÓN BÁSICA Y APARIENCIA
" ============================================================================
syntax on                       " Activa el resaltado de colores por defecto
set number                      " Muestra los números de línea lateral
set relativenumber              " Números relativos (ideal para saltos rápidos)
set mouse=a                     " Permite usar el ratón para cliquear y hacer scroll
set termguicolors               " Soporte para colores verdaderos de 24 bits
set background=dark             " Optimiza los colores para fondos oscuros

" ============================================================================
" SINTAXIS AUTOMÁTICA Y SOPORTE DE ARCHIVOS
" ============================================================================
filetype plugin indent on       " Detecta tipos de archivo, carga plugins e indentación

" Forzar que los archivos con extensión .md se abran siempre como Markdown
autocmd BufNewFile,BufRead *.md set filetype=markdown

" Activar corrector ortográfico en español automáticamente al abrir Markdown
autocmd FileType markdown setlocal spell spelllang=es

" ============================================================================
" TABULACIONES Y ESPACIADO (Configuración limpia para código y texto)
" ============================================================================
set tabstop=4                   " Una tabulación visual equivale a 4 espacios
set shiftwidth=4                " Tamaño de la indentación automática
set expandtab                   " Convierte las tabulaciones en espacios al escribir
set smartindent                 " Indentación inteligente automática

" ============================================================================
" BÚSQUEDA Y NAVEGACIÓN
" ============================================================================
set hlsearch                    " Resalta todas las coincidencias de búsqueda
set incsearch                   " Resalta los resultados mientras vas escribiendo
set ignorecase                  " Ignora mayúsculas al buscar texto
set smartcase                   " Si usas una mayúscula, desactiva 'ignorecase'
set scrolloff=8                 " Mantiene 8 líneas visibles arriba/abajo al hacer scroll

```