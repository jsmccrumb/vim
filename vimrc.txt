" use ' ' as <leader>
let mapleader = " "
" run pathogen
execute pathogen#infect()

" set filetypes as typescriptreact
autocmd BufNewFile,BufRead *.tsx,*.jsx set filetype=typescriptreact

" some recomendations from pathogen...
syntax on
filetype plugin indent on

" NERDTREE stuff
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 0 && !exists("s:std_in") | NERDTree | endif

" useful defaults
set ruler
set hlsearch
set incsearch
set showmatch
set noerrorbells
set novisualbell

" Enable 256 colors palette in Gnome Terminal
if $COLORTERM == 'gnome-terminal'
  set t_Co=256
endif
set background=dark

set encoding=utf8
set ffs=unix,dos,mac

set nobackup
set nowb

set expandtab
set smarttab
set shiftwidth=2
set tabstop=2
set ai
set si
set number
set signcolumn=number

" Easier movement between split windows CTRL + {h, j, k, l}
nnoremap <c-h> <c-w>h
nnoremap <c-j> <c-w>j
nnoremap <c-k> <c-w>k
nnoremap <c-l> <c-w>l
inoremap <tab> <c-n>

" CoC extensions
let g:coc_global_extensions = ['coc-tsserver', 'coc-json']

" Add CoC Prettier if prettier is installed
if isdirectory('./node_modules') && isdirectory('./node_modules/prettier')
  let g:coc_global_extensions += ['coc-prettier']
endif

" Add CoC ESLint if ESLint is installed
if isdirectory('./node_modules') && isdirectory('./node_modules/eslint')
  let g:coc_global_extensions += ['coc-eslint']
endif

nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gy <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)
nmap <silent> gr <Plug>(coc-references)

" Remap keys for applying codeAction to the current buffer.
nmap <leader>ac  <Plug>(coc-codeaction)

" turn off highlights on leader enter
map <silent> <leader><cr> :noh<cr>

" statusline stuff
set laststatus=2

set statusline=%f                                " filename                                                                                                                                                  
set statusline+=%m                               " modified flag
set statusline+=%r                               " readonly flag
set statusline+=\                                " spacer                                                                                                                                            
set statusline+=%4l/%-4L                         " line / lines minwidth 4
set statusline+=%=                               " switch to right side
set statusline+=%{FugitiveStatusline()}          " indicator including the current branch and the currently edited file's commit


" vim-javascript
let g:javascript_plugin_jsdoc = 1

" color fixes
hi Pmenu ctermbg=darkgrey
hi FgCocHintFloatBgCocFloating ctermfg=12 ctermbg=darkgrey
hi FgCocWarningFloatBgCocFloating ctermfg=13 ctermbg=darkgrey

" cursor 6 = solid line
" 5 = blinking line
let &t_SI = "\e[5 q"
let &t_EI = "\e[6 q"
