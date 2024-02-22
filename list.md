Basic vimrc configuration list
----------------------------------------


### 1 - Basic
```
set nocompatible " Use VIM settings rather than 
                 " Vi settings; this *must* be
                 " first in .vimrc 

syntax enable  "keeps your current color settings
syntax on      "highlight syntax permanently

filetype plugin indent on

set number          " numbered lines (set nu)
set autoindent      " auto-identacao (set ai)
set cindent         " revolves around the recoil style (set ci cindent)
set shiftwidth=4    " creates 4 spaces in the tab
set tabstop=4       " changes the width of tab
set softtabstop=4   " option to cause <Tab> and <BS> to the correct number of spaces 
set expandtab       " creates spaces instead of tab
set showmatch       " shows the beginning of a new closed block {  },[  ], (  ) (set sm)
set incsearch       " increases search (set is)
set hlsearch        " Highlight search (set hls)
set smartcase       " considers uppercase of lowercase (set smartcase scs)
set hidden          " Hide buffers when they are abandoned
set nobackup        " no backup
set noswapfile      " no swap file
set nowritebackup   " no write backup
set mouse=a         " Enable mouse usage (all modes)
set showcmd         " Show (partial) command in status line.
set ruler           " ruler
set linebreak       " does not share the word EOL
set visualbell      " disable beep
set path+=**        " find files with :find myfile.txt
set scrolloff=0     " Lines visible above or below the cursor 
set clipboard=unnamedplus "copy to clipboard
set completeopt=longest,menuone
"set background=dark " background
"set makeprg=php\ -1\ %
"set errorformat=%m\ in\ %f\ on\ line\ %1
"set foldmethod=indent
"set foldminlines=5
```

### 2 - AUTOCOMPLETE in specific languages
```
"
" AUTOCOMPLETE in specific languages
" ----------------------------------------
"
autocmd FileType php        setlocal omnifunc=phpcomplete#CompletePHP
autocmd FileType html       setlocal omnifunc=htmlcomplete#CompleteTags
autocmd FileType css        setlocal omnifunc=csscomplete#CompleteCSS
autocmd FileType javascript setlocal omnifunc=javascriptcomplete#CompleteJS
autocmd FileType python     setlocal omnifunc=pythoncomplete#Complete
autocmd FileType ruby       setlocal omnifunc=rubycomplete#Complete
autocmd FileType xml        setlocal omnifunc=xmlcomplete#CompleteTags
autocmd FileType c          setlocal omnifunc=ccomplete#Complete
autocmd FileType cpp        setlocal omnifunc=omni#cpp#complete#Main
autocmd FileType hpp        setlocal omnifunc=omni#cpp#complete#Main
```

### 3 - AUTOCMD by file type
```
"
" AUTOCMD by file type
" ----------------------------------------
"
if has("autocmd")
autocmd BufEnter *.phtml set syn=php    " Files found ZendFramework
autocmd BufEnter *.ctp set syn=php      " Files found CackePHP
autocmd BufRead,BufNewFile,BufReadPost *.php set filetype=php.html
autocmd BufRead,BufNewFile,BufReadPost *.cpp set filetype=cpp.c
autocmd BufRead,BufNewFile,BufReadPost *.twig set filetype=twig.html 
endif
```

### 4 - DISABLE arrow keys
```
"
" DISABLE arrow keys
" ----------------------------------------
"
noremap <up> <nop>
noremap <down> <nop>
noremap <left> <nop>
noremap <right> <nop>
inoremap <up> <nop>
inoremap <down> <nop>
inoremap <left> <nop>
inoremap <right> <nop>
```

### 5 - Automatic CLOSING
```
"
" Automatic CLOSING
" ----------------------------------------
"
inoremap '' ''
inoremap `` ``
inoremap "" ""
inoremap () ()
inoremap [] []
inoremap {} {}

inoremap ( ()<left>
inoremap { {}<left>
inoremap [ []<left>
inoremap ' ''<left>
inoremap " ""<left>
inoremap ` ``<left>

inoremap '; '';<left><left>
inoremap `; ``;<left><left>
inoremap "; "";<left><left>
inoremap (; ();<left><left>
inoremap [; [];<left><left>
inoremap {; {};<left><left>

inoremap ', '',<left><left>
inoremap `, ``,<left><left>
inoremap ", "",<left><left>
inoremap (, (),<left><left>
inoremap [, [],<left><left>
inoremap {, {};<left><left>

inoremap (<CR> (<CR>)<ESC>O<TAB>
inoremap (;<CR> (<CR>);<ESC>O<TAB>
inoremap [<CR> [<CR>]<ESC>O<TAB>
inoremap [;<CR> [<CR>];<ESC>O<TAB>
inoremap {<CR> {<CR>}<ESC>O<TAB>
inoremap {;<CR> {<CR>};<ESC>O<TAB>
```

### 6 - SHORTCUTS 
```
"
" SHORTCUTS 
" ----------------------------------------
"
noremap <leader>w :w!<cr>
noremap <leader>W :wa!<cr>
inoremap <leader>w <c-o>:w!<cr>
inoremap <leader>W <c-o>:wa!<cr>
```

### 7 - HIGHLIGHT WORD under the cursor
```
" HIGHLIGHT WORD under the cursor
noremap <leader>hw :let @/="<C-r><C-w>"<cr>

" CLEAR buffer search 
noremap <leader>hc :let @/=''<cr>
```

### 8 - LOWERCASE
```
"
" LOWERCASE
" ----------------------------------------
"
cab W w|cab Q q|cab B b
cab LS ls|cab Ls ls|cab lS ls
cab PWD pwd|cab Pwd pwd
cab Wq wq|cab wQ wq|cab WQ wq|cab Wa wa|cab WA wa|cab wA wa
cab WALL wall|cab Wall wall|cab wALL wall
cab QALL qall|cab Qall qall|cab qALL qall|cab QA qa|cab qA qa
cab WQALL wqall|cab wQALL wqall|cab Wqall wqall
cab BN bn|cab Bn bn|cab bN bn
cab BD bd|cab Bd bd|cab bD bd
```

### 9 - REMOVE the TAGS and keep the text
```
" REMOVE the TAGS and keep the text
cab rm_tag %s#<[^>]\+>##g
```

### 10 - HIGHLIGHT cursor line
```
" HIGHLIGHT cursor line
set cul
hi cursorline cterm=NONE ctermbg=black guibg=lightgrey
```

### 11 - LOAD VIMRC without closing the editor
```
" LOAD VIMRC without closing the editor
map ,u :source /etc/vim/vimrc<CR>:echo ' VIMRC global loaded!'<CR>
" map ,u :source ~/.vim/vimrc<CR>:echo ' VIMRC local reloaded!'<CR>
" map ,u :source ~/vimfiles/vimrc<CR>:echo ' VIMRC vimfiles reloaded!'<CR>
```


