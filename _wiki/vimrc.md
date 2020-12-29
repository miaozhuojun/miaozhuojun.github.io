---
layout: wiki
title: vim配置
categories: vim
description: vim配置
keywords: vim，配置
---

#### 以下是个人的vimrc配置，会不断更新

```vim
echo ">^.^<"

set noshowmatch

set nocompatible
filetype plugin on

" Add vim-plug
call plug#begin('$HOME\vimfiles\plugin')
Plug 'gabrielelana/vim-markdown'
call plug#end()

" disable autogeneration of un~ & ~ files
set noundofile
set nobackup

" vimscript practice
set number

" Basic Mapping
map - dd<ESC>p
map _ :m .-2<CR>
unmap -
unmap _

" Modal Mapping
imap <c-u> <esc>viwUi
nmap <c-u> viwU
iunmap <c-u>
nunmap <c-u>

" Strict Mapping
inoremap <c-u> <esc>viwUA
iunmap <c-u>

" Leaders
let maplocalleader = "\\"
inoremap <localleader>u <esc>viwUA
iunmap <localleader>u

" Editing Your Vimrc
nnoremap <localleader>ev :vsplit $MYVIMRC<cr>
nnoremap <localleader>sv :source $MYVIMRC<cr>

" More Mappings
nnoremap <leader>" viw<esc>a"<esc>bi"<esc>lel

nnoremap <leader>m viw<esc>a`$<esc>bbi$`<esc>f$
vnoremap <leader>m <esc>a`$<esc>gvo<esc>i$`<esc>f$

nnoremap <leader>b viw<esc>a*<esc>bi*<esc>lel
vnoremap <leader>b <esc>a*<esc>gvo<esc>i*<esc>lel

" Set editor font
set guifont=Consolas:h11

" highlight cursor row
set cursorline
" highlight cursor col
set cursorcolumn

" Set char encoding
set encoding=utf-8
set fileencodings=utf-8,gb18030,utf-16,big5 

inoremap jk <esc>
inoremap <esc> <nop>

autocmd FileType java  nnoremap <buffer> <localleader>c I// <esc>
autocmd FileType c     nnoremap <buffer> <localleader>c I// <esc>
autocmd FileType c++   nnoremap <buffer> <localleader>c I// <esc>
autocmd FileType shell nnoremap <buffer> <localleader>c I# <esc>
```
