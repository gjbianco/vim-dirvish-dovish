# 🧰 vim-dirvish-dovish

> The file manipulation commands for [vim-dirvish][dirvish] that you've always wanted

This variant makes several preferential changes to the plugin.

## Installation & Requirements

You'll need:

- [dirvish.vim][dirvish]

Then install with your favorite package manager:

```vim
Plug 'gjbianco/vim-dirvish-dovish', {'branch': 'main'}
```

## Mappings

| Function                                | Default | Key                               |
| --------------------------------------- | ------- | --------------------------------- |
| Create file                             | `a`     | `<Plug>(dovish_create_file)`      |
| Create directory                        | `A`     | `<Plug>(dovish_create_directory)` |
| Delete under cursor                     | `dd`    | `<Plug>(dovish_delete)`           |
| Rename under cursor                     | `r`     | `<Plug>(dovish_rename)`           |
| Yank under cursor (or visual selection) | `yy`    | `<Plug>(dovish_yank)`             |
| Copy file to current directory          | `pp`    | `<Plug>(dovish_copy)`             |
| Move file to current directory          | `PP`    | `<Plug>(dovish_move)`             |
| Reload the files in current directory   | `C-r`   | `<Plug>(dovish_reload)`           |

You can unmap all of the maps above and set your own (mine are below). Add this to `ftplugin/dirvish.vim`:

```vim
" unmap all default mappings
let g:dirvish_dovish_map_keys = 0

" unmap dirvish default
unmap <buffer> p

" Your preferred mappings
nmap <silent><buffer> i <Plug>(dovish_create_file)
nmap <silent><buffer> I <Plug>(dovish_create_directory)
nmap <silent><buffer> dd <Plug>(dovish_delete)
nmap <silent><buffer> r <Plug>(dovish_rename)
nmap <silent><buffer> yy <Plug>(dovish_yank)
xmap <silent><buffer> yy <Plug>(dovish_yank)
nmap <silent><buffer> p <Plug>(dovish_copy)
nmap <silent><buffer> P <Plug>(dovish_move)
nmap <silent><buffer> <C-r> <Plug>(dovish_reload)
```

## Customize Commands

Most file operations can be customized. Below are the defaults:

```vim
" Used for <Plug>(dovish_yank)
function! g:DovishCopyFile(target, destination) abort
  return 'cp ' . a:target . ' ' . a:destination
endfunction

" Used for <Plug>(dovish_yank)
function! g:DovishCopyDirectory(target, destination) abort
  return 'cp -r' . a:target . ' ' . a:destination
endfunction

" Used for <Plug>(dovish_move)
function! g:DovishMove(target, destination) abort
  return 'mv ' . a:target . ' ' . a:destination
endfunction

" Used for <Plug>(dovish_delete)
function! g:DovishDelete(target) abort
  return 'rm ' . a:target
endfunction

" Used for <Plug>(dovish_rename)
function! g:DovishRename(target, destination) abort
  return 'mv ' . a:target . ' ' . a:destination
endfunction
```

[dirvish]: https://github.com/justinmk/vim-dirvish

## Credit

Thanks to [justinmk](https://github.com/roginfarrer) for writing the [original version](https://github.com/roginfarrer/vim-dirvish-dovish) of this plugin!
