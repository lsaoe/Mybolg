# Mybolg
set nocompatible              " be iMproved, required
filetype on                   " required

"set spelllang=en
"set spell
set tags=/Users/lsaoe/tags
set linebreak
"set nowrap
set autoindent
set smartindent
set t_Co=256
set wrap
" set the runtime path to include Vundle and initialize
" set cursorline
set background=dark
"colorscheme solarized
"colorscheme desert
colorscheme molokai
"colorscheme luna
"colorscheme quantum
syntax on

if !has('gui_running')
  set term=screen-256color
endif
if (has("termguicolors"))
  set termguicolors
  let &t_8f = "\<esc>[38;2;%lu;%lu;%lum"
  let &t_8b = "\<esc>[48;2;%lu;%lu;%lum"
endif

set rtp+=~/.vim/bundle/Vundle.vim
set runtimepath^=~/.vim/bundle/ctrlp.vim

call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
Plugin 'ascenator/L9', {'name': 'newL9'}

Plugin 'Valloric/YouCompleteMe'
Plugin 'CodeFalling/fcitx-vim-osx'
" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line


set fileencodings=utf-8
set fileencoding=utf-8
set encoding=utf8

set backspace=indent,start
set expandtab
set shiftwidth=2
set softtabstop=2
set tabstop=2
set listchars=eol:¬
set number
set autoindent
set hlsearch
set incsearch
" highlight Normal ctermfg=white ctermbg=cyan
syntax enable

let g:proj_window_width=5
set laststatus=2


map <C-T> :FufFile<CR>
map <C-E> :MRU<CR>
map <C-S-M> :Emodel<CR>
map <C-S-C> :Econtroller<CR>
map <C-S-U> :Eunit<CR>
map <C-S-L> :Efunctional<CR>
"map <C-V> :Eview<CR>
"map <C-H> :Ehelper<CR>
"map <C-J> :ZoomWin<CR>

" Shift pane
map <C-H> <C-W>h
map <C-J> <C-W>j
map <C-K> <C-W>k
map <C-L> <C-W>l


" Strip trailing whitespace
function! <SID>StripTrailingWhitespaces()
    " Preparation: save last search, and cursor position.
    let _s=@/
    let l = line(".")
    let c = col(".")
    " Do the business:
    %s/\s\+$//e
    " Clean up: restore previous search history, and cursor position
    let @/=_s
    call cursor(l, c)
endfunction
autocmd BufWritePre * :call <SID>StripTrailingWhitespaces()

" match Todo /\s\+$/
filetype plugin on
let mapleader = ","

" THE VIM OUTLINER (TVO)
" defaults:
let otl_install_menu=1
let no_otl_maps=0
let no_otl_insert_maps=0

" overrides:
let otl_bold_headers=0
let otl_use_thlnk=0

" au BufWinLeave *.otl mkview
" au BufWinEnter *.otl silent loadview
let maplocalleader = ","

""Only do this part when compiled with support for autocommands.
"if has("autocmd")
"  autocmd Filetype java setlocal omnifunc=javacomplete#Complete
"endif


set nocompatible               " be iMproved
" filetype off                   " required!




" ============== Vundle part =================
set rtp+=~/.vim/bundle/vundle/
call vundle#rc()

" let Vundle manage Vundle
" required!

" My Bundles here:
"
" original repos on github
Bundle 'tpope/vim-fugitive'
Bundle 'Lokaltog/vim-easymotion'
Bundle 'tpope/vim-rails.git'
Bundle 'tsaleh/vim-matchit.git'
Bundle 'ecomba/vim-ruby-refactoring.git'

" vim-scripts repos
Bundle 'L9'
Bundle 'FuzzyFinder'

Bundle 'YankRing.vim'
Bundle 'vividchalk.vim'
Bundle 'The-NERD-Commenter'
Bundle 'The-NERD-tree'
Bundle 'kchmck/vim-coffee-script'
Bundle 'Valloric/YouCompleteMe'
Bundle 'mileszs/ack.vim'
Plugin 'CodeFalling/fcitx-vim-osx'
let g:ackprg = 'ag --nogroup --nocolor --column'

Bundle 'flazz/vim-colorschemes'
Bundle 'mru.vim'
Bundle 'greplace.vim'

filetype plugin indent on     " required!
"
" Brief help
" :BundleList          - list configured bundles
" :BundleInstall(!)    - install(update) bundles
" :BundleSearch(!) foo - search(or refresh cache first) for foo
" :BundleClean(!)      - confirm(or auto-approve) removal of unused bundles
"
" see :h vundle for more details or wiki for FAQ
" NOTE: comments after Bundle command are not allowed..

map <c-u> :Ack<space>
map <S-F> <Leader><Leader>f
map <Leader>a :YRShow<CR>
map <Leader>t :NERDTree<CR>
map <Leader>q :q<CR>
map <Leader>f :Rfixture<CR>
map <Leader>rj :Rjavascript<CR>

" let g:ycm_global_ycm_extra_conf = 'your path to .ycm_extra_conf.py'
set guifont=Monaco:h16
set guicursor+=a:blinkon0
set spell
set noswapfile
"if has("gui_macvim")
"  " Press Ctrl-Tab to switch between open tabs (like browser tabs) to
"  " the right side. Ctrl-Shift-Tab goes the other way.
"  noremap <C-Tab> :tabnext<CR>
"  noremap <C-S-Tab> :tabprev<CR>
"
"  " Switch to specific tab numbers with Command-number
"  noremap <D-1> :tabn 1<CR>
"  noremap <D-2> :tabn 2<CR>
"  noremap <D-3> :tabn 3<CR>
"  noremap <D-4> :tabn 4<CR>
"  noremap <D-5> :tabn 5<CR>
"  noremap <D-6> :tabn 6<CR>
"  noremap <D-7> :tabn 7<CR>
"  noremap <D-8> :tabn 8<CR>
"  noremap <D-9> :tabn 9<CR>
"  " Command-0 goes to the last tab
"  noremap <D-0> :tablast<CR>
"endif
cnoremap <C-p> <Up>
cnoremap <C-n> <Down>
cnoremap <C-b> <Left>
cnoremap <C-f> <Right>

let g:molokai_original = 1
