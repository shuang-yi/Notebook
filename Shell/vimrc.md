# .vimrc

```
"-----HELP:-------------------------------------------- !--{{
" - - - display the vim PATH
"   :set runtimepath?
"   $VIM : where vim is installed
"   $VIMRUNTIME : configure file path
"   .vim : user configure file path, goes first in RUNTIMEPATH
" - - - check configure
"   :map      :   all maps
"   :command  :   all commands
" !--}}
" verbose >= 12 if you want to see details



"-pathogen	( plug-in manager )
"execute pathogen#infect() 	

set verbose=0
set nocompatible
set shell=zsh\ -i

"- - - - - - - - - - - - - - -
"- - - - - basic setting	!---{{
"operate
inoremap jk <esc>
"search
set incsearch
set hlsearch
noremap <Leader>, :nohl<cr>
set ignorecase smartcase	"ignore the case when searching in a smart way
"fold
set foldmethod=marker
set foldmarker={{,}}
set foldlevelstart=0
"typing
set scrolloff=3
set tabstop=4	"number of spaces a <Tab> in the text stands for
set shiftwidth=2	"number of spaces used for each step of (auto)indent
set softtabstop=4	"if non-zero, number of spaces to insert for a <Tab>
set laststatus=2	"0, 1 or 2; when to use a status line for the last window
set backspace=indent,eol,start	"backspace and delete can delete <cr> in insert mode

"##outlook
set cursorline
set showcmd
hi cursorline cterm=NONE ctermbg=white
syntax on
filetype plugin indent on
set ruler
set number
set statusline=%<%f\ %h%m%r%=%-14.(%l,%c%V%)\ [%L]:%P
set guitablabel=(%N)%t
" colorscheme molokai
```

# Other setting

```
"##performance
"set hidden	"donot unload buffer when it is abandoned
" remember last position
au BufReadPost * if line("'\"") > 0|if line("'\"") <= line("$")|exe("norm '\"")|else|exe "norm $"|endif|endif

"##gui
if has ('x') && has ('gui') " on Linux use + register for copy-paste
  set clipboard=unnamedplus
elseif has ('gui') " one mac and windows, use * register for copy-paste
  "clipboard
  set clipboard=unnamed
  "font
  set guifont=Monaco:h14
  "colorscheme
  let g:solarized_termcolors=256
  color solarized                 " load a colorscheme
  let g:solarized_termtrans=1
  let g:solarized_contrast="high"
  let g:solarized_visibility="high"
  set transparency=5          " Make the window slightly transparent
endif

"---}}

"fortran
"au BufReadPost *.f90  let fortran_free_source=1
"autocmd BufRead *.f90 source ~/.vim/myfiles/fortran.vim

"- - - - - map, command, autocmd	---{{
"##map
let mapleader=","
"noremap <silent> <leader>
noremap <leader>q A<tab>!---{{<esc>
noremap <leader>Q A<tab>!---}}<esc>
inoremap ,-- - - - - -
noremap <leader>1 :set foldlevel=0<cr>
noremap <leader>2 :set foldlevel=1<cr>
noremap <leader>3 :set foldlevel=2<cr>
noremap <leader>0 :set foldlevel=99<cr>

"##command
:command! -nargs=0 Viba :tabnew ~/.vimrc
:command! -nargs=0 Vitmp :tabnew /tmp/tmp
:command! -nargs=0 W :w
:command! -nargs=0 Wq :wq
:command! -nargs=0 Q :q
:command! -nargs=0 Soba :source ~/.vimrc
:command! -nargs=+ Say :echo "<args>"
:autocmd! bufwritePost .vimrc source ~/.vimrc
"---}}

"- - - - - plugin	!---{{

"nerdcommenter
map <c-h> ,c<space> 
" <leader>ci	toggle the comment state of the selected line(s) individually
 "<leader>cA	go to the end of current line and enter comment mode

"nerdtree
"map <c-e> :NERDTreeToggle<cr>
"let loaded_nerd_tree=1    "disable nerdtree if 1
"let NERDTreeIgnore=['/.vim$','/~$']    "ignore special type
let NERDTreeShowHidden=0    "show hidden files 
"let NERDTreeSortOrder=['*.f90$','*.for$','*.f77$','*.dat$', '*']    "sort order
let NERDTreeCaseSensitiveSort=0     "sort regardless of case
let NERDTreeWinSize=30
let NERDTreeShowLineNumbers=1
let NERDTreeShowBookmarks=1
let NERDTreeQuitOnOpen=1    "if nerdtree is the only window open, close it
let NERDTreeHighlightCursorline=1     "highlight cursor line
"nmap <silent> <leader>tmk :Bookmark expand(/"<cword>/")<cr>

"Tagbar
noremap <Leader>ta :TagbarToggle<cr>

"CtrlP
set runtimepath^=~/.vim/bundle/ctrlp.vim
let g:ctrlp_map = '<c-p>'
let g:ctrlp_cmd = 'CtrlP'
let g:ctrlp_working_path_mode = 'ra'
set wildignore+=*/tmp/*,*.so,*.swp,*.zip     " MacOSX/Linux
set wildignore+=*\\tmp\\*,*.swp,*.zip,*.exe  " Windows
"
let g:ctrlp_custom_ignore = '\v[\/]\.(git|hg|svn)$'
"let g:ctrlp_custom_ignore = {
  "\ 'dir':  '\v[\/]\.(git|hg|svn)$',
  "\ 'file': '\v\.(exe|so|dll)$',
  "\ 'link': 'some_bad_symbolic_links'
  "\ }
let g:ctrlp_user_command = 'find %s -type f'        " MacOSX/Linux
"let g:ctrlp_user_command = 'dir %s /-n /b /s /a-d'  " Windows

"vim-cmdline
"let g:Powerline_symbols = 'fancy'
"
"neocomplcatch
let g:neocomplcache_enable_at_startup = 1
"
"mark
"m, place the next available mark
"m<space> delete all mark
"]` jump to next
"`] jump by alphabetical order
"---}}

"filelist
"~/.vim/bundle/snipmate-snippets/snippets/fortran.snippets
"~/.vim/bundle/fortran/ftplugin/fortran.vim
"~/.vim/bundle/fortran/after/indent/fortran.vim
```

