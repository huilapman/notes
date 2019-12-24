## Install Python3 with Proxy

    /etc/yum.conf
    
    [main]
    cachedir=/var/cache/yum/$basearch/$releasever
    keepcache=0
    debuglevel=2
    logfile=/var/log/yum.log
    exactarch=1
    obsoletes=1
    gpgcheck=1
    plugins=1
    installonly_limit=3
    sslverify=false
    
    #  This is the default, if you make this bigger yum won't see if the metadata
    # is newer on the remote and so you'll "gain" the bandwidth of not having to
    # download the new metadata and "pay" for it by yum not having correct
    # information.
    #  It is esp. important, to have correct metadata, for distributions like
    # Fedora which don't keep old packages around. If you don't like this checking
    # interupting your command line usage, it's much better to have something
    # manually check the metadata once an hour (yum-updatesd will do this).
    # metadata_expire=90m
    
    # PUT YOUR REPOS HERE OR IN separate files named file.repo
    # in /etc/yum.repos.d
    #
    # The Enable yum via proxy server
    #
    #proxy=http://192.168.235.164:3128
    #proxy_username=yum-user
    #proxy_password=qwerty
    proxy=http://192.168.32.22:3128


## Bashrc
    ~/.bashrc
    
    export http_proxy="http://192.168.32.22:3128"
    export https_proxy="http://192.168.32.22:3128"
    export no_proxy="localhost,127.0.0.1"
    export LANG=en_US.UTF-8


## Setup Virtual Environment
    
    python3 -m venv <venv_name>

    
## PIP install package with proxy

    pip3 install --trusted-host pypi.org --trusted-host files.pythonhosted.org --trusted-host pypi.python.org requests
    pip3 install --trusted-host pypi.org --trusted-host files.pythonhosted.org --trusted-host pypi.python.org flake8
    pip3 install --trusted-host pypi.org --trusted-host files.pythonhosted.org --trusted-host pypi.python.org autopep8
    pip3 install --trusted-host pypi.org --trusted-host files.pythonhosted.org --trusted-host pypi.python.org --upgrade pip
    

    
## VIM Python IDE Plugin Install disable SSL cert checking
    
    git config --global http.sslVerify "false"
    
    
## VIM .vimrc

    set nocompatible
    syntax on
    filetype plugin indent on
    set ic
    set hlsearch
    set encoding=utf-8
    set fileencodings=utf-8
    set cursorline
    set autoindent
    set smartindent
    set scrolloff=4
    set showmatch
    set nu
    
    
    nnoremap <C-J> <C-W><C-J>
    nnoremap <C-K> <C-W><C-K>
    nnoremap <C-L> <C-W><C-L>
    nnoremap <C-H> <C-W><C-H>
    
    
    let python_highlight_all=1
    au Filetype python set tabstop=4
    au Filetype python set softtabstop=4
    au Filetype python set shiftwidth=4
    au Filetype python set textwidth=79
    au Filetype python set expandtab
    au Filetype python set autoindent
    au Filetype python set fileformat=unix
    autocmd Filetype python set foldmethod=indent
    autocmd Filetype python set foldlevel=99
    
    
    " set the runtime path to include Vundle and initialize
    set rtp+=~/.vim/bundle/Vundle.vim
    call vundle#begin()
    
    " alternatively, pass a path where Vundle should install plugins
    "call vundle#begin('~/some/path/here')
    
    " let Vundle manage Vundle, required
    Plugin 'gmarik/Vundle.vim'
    Plugin 'Chiel92/vim-autoformat'
    Plugin 'tmhedberg/simpylfold'
    Plugin 'scrooloose/nerdtree'
    Plugin 'kien/rainbow_parentheses.vim'
    Plugin 'bling/vim-airline'
    Plugin 'scrooloose/syntastic'
    
    
    " add all your plugins here (note older versions of Vundle
    " used Bundle instead of Plugin)
    
    " ...
    
    " All of your Plugins must be added before the following line
    call vundle#end()            " required
    filetype plugin indent on    " required
    
    
    nnoremap <F6> :Autoformat<CR>
    let g:autoformat_autoindent = 0
    let g:autoformat_retab = 0
    let g:autoformat_remove_trailing_spaces = 0
    
    
    nnoremap <F3> :NERDTreeToggle<CR>
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif
    
    
    let g:rbpt_colorpairs = [
                            \ ['brown',       'RoyalBlue3'],
                            \ ['Darkblue',    'SeaGreen3'],
                            \ ['darkgray',    'DarkOrchid3'],
                            \ ['darkgreen',   'firebrick3'],
                            \ ['darkcyan',    'RoyalBlue3'],
                            \ ['darkred',     'SeaGreen3'],
                            \ ['darkmagenta', 'DarkOrchid3'],
                            \ ['brown',       'firebrick3'],
                            \ ['gray',        'RoyalBlue3'],
                            \ ['darkmagenta', 'DarkOrchid3'],
                            \ ['Darkblue',    'firebrick3'],
                            \ ['darkgreen',   'RoyalBlue3'],
                            \ ['darkcyan',    'SeaGreen3'],
                            \ ['darkred',     'DarkOrchid3'],
                            \ ['red',         'firebrick3'],
                            \ ]
    let g:rbpt_max = 16
    let g:rbpt_loadcmd_toggle = 0
    au VimEnter * RainbowParenthesesToggle
    au Syntax * RainbowParenthesesLoadRound
    au Syntax * RainbowParenthesesLoadSquare
    au Syntax * RainbowParenthesesLoadBraces
    
    set statusline+=%#warningmsg#
    set statusline+=%{SyntasticStatuslineFlag()}
    set statusline+=%*
    let g:syntastic_always_populate_loc_list = 1
    let g:syntastic_auto_loc_list = 1
    let g:syntastic_check_on_open = 1
    let g:syntastic_check_on_wq = 0


## Bookmarks

    https://vimawesome.com
    https://dev.to/bezirganyan/editor-wars-vim-as-a-perfect-python-ide-19ne
    https://realpython.com/vim-and-python-a-match-made-in-heaven/
    https://zhuanlan.zhihu.com/p/30022074
    https://scrapy.org/
