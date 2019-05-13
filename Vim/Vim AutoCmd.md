---
title: Vim AutoCmd
tags: Vim
grammar_cjkRuby: true
grammar_tableExtra: true
---
```vim
:autocmd BufNewFile * :write
```

* Event watching:
	* Events:
		1. Edit a file
		2. Read a file
		3. Switching filetype setting
		4. Press a key a few times
		5. Enter insert mode
		6. Exit insert mode

* Multiplue Events: use `setlocal` when read or write some buffers.
```vim
:autocmd BufWritePre, BufRead *.html :normal gg=G
```

* FileType Events: when vim set a buffer's filetype.
```vim
:autocmd FileType python setlocal nowrap
```

* Autocmd groups.
	* use autocmd! to cancel befored autocmd in one group

```vim
:augroup testgroup
:	autocmd BufWrite * :echom "BAZ"
:	autocmd BufWrite * :echom "Foo"
:augroup END
:augroup testgroup
:	autocmd! " cancel before autocmds
:	autocmd BufWrite * :echo "Cat"
:augroup END
```
