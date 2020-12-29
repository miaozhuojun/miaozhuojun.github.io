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
