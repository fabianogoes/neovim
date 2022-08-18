# Neovim

<aside>
💡 https://github.com/fabianogoes/neovim

</aside>

## Instalação

### Dependências de SO

```bash
sudo apt update -y && sudo apt upgrade -y && \
sudo apt install -y git curl wget git zsh vim tree zip unzip autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm6 libgdbm-dev libdb-dev xclip fd-find python3-pip ack-grep nodejs npm neofetch && \
sudo apt autoremove -y && sudo apt autoclean -y
```

### Python3:

```bash
pip3 install --user neovim jedi psutil setproctitle
```

### Node

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash

nvm list-remote
nvm install --lts
node --version

npm install -g neovim
```

### Dracula KDE - Konsole

Download

[dracula-theme-for-konsole.zip](Neovim%2070a57143355f4b24a491505bbcd27f11/konsole-master.zip)

**Activating theme**

1. Copy `Dracula.colorscheme` to `~/.local/share/konsole`
2. Go to *Konsole > Settings > Edit Current Profile… > Appearance* tab
3. Select the *Dracula* scheme from the *Color Schemes & Background…* pane

### Powerlevel10k

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k && echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >> ~/.zshrc
```

### Download

‣

### Instalando por pacote `.deb`

```bash
chmod +x nvim-linux64.deb
sudo apt install ./nvim-linux64.deb
```

## Configurações

```bash
mkdir ~/.config/nvim && mkdir ~/.config/nvim/autoload && mkdir ~/.config/nvim/vim-plug && ~/.config/nvim/keys && mkdir ~/.config/nvim/plug-config

touch ~/.config/nvim/settings.vim && \
touch ~/.config/nvim/init.vim && \
touch ~/.config/nvim/autoload/plug.vim && \
touch ~/.config/nvim/vim-plug/plugins.vim && \
touch ~/.config/nvim/keys/mappings.vim && \
touch ~/.config/nvim/plug-config/telescope.vim
```

- `~/.config/nvim/settings.vim`
    
    ```
    " set leader key
    let g:mapleader = "\<Space>"
    
    syntax enable                           " Enables syntax highlighing
    set hidden                              " Required to keep multiple buffers open multiple buffers
    set nowrap                              " Display long lines as just one line
    set encoding=utf-8                      " The encoding displayed
    set pumheight=10                        " Makes popup menu smaller
    set fileencoding=utf-8                  " The encoding written to file
    set ruler              			            " Show the cursor position all the time
    set cmdheight=2                         " More space for displaying messages
    set iskeyword+=-                      	" treat dash separated words as a word text object
    set mouse=a                             " Enable your mouse
    set splitbelow                          " Horizontal splits will automatically be below
    set splitright                          " Vertical splits will automatically be to the right
    set t_Co=256                            " Support 256 colors
    set conceallevel=0                      " So that I can see `` in markdown files
    set tabstop=4                           " Insert 2 spaces for a tab
    set shiftwidth=2                        " Change the number of space characters inserted for indentation
    set smarttab                            " Makes tabbing smarter will realize you have 2 vs 4
    set expandtab                           " Converts tabs to spaces
    set smartindent                         " Makes indenting smart
    set autoindent                          " Good auto indent
    set laststatus=0                        " Always display the status line
    set number                              " Line numbers
    set cursorline                          " Enable highlighting of the current line
    set background=dark                     " tell vim what the background color looks like
    set showtabline=2                       " Always show tabs
    set noshowmode                          " We don't need to see things like -- INSERT -- anymore
    set nobackup                            " This is recommended by coc
    set nowritebackup                       " This is recommended by coc
    set updatetime=300                      " Faster completion
    set timeoutlen=500                      " By default timeoutlen is 1000 ms
    set formatoptions-=cro                  " Stop newline continution of comments
    set clipboard+=unnamedplus
    set relativenumber
    set encoding=utf8
    
    set completeopt=menuone,noselect
    
    filetype plugin on
    
    au! BufWritePost $MYVIMRC source %      " auto source when writing to init.vm alternatively you can run :source $MYVIMRC
    
    " You can't stop me
    cmap w!! w !sudo tee %
    
    let g:markdown_fenced_languages = [
          \ 'vim',
          \ 'help'
          \]
    ```
    
    [settings.vim](Neovim%2070a57143355f4b24a491505bbcd27f11/settings.vim)
    

## Plugin

[plugins.vim](Neovim%2070a57143355f4b24a491505bbcd27f11/plugins.vim)

- → `~/.config/nvim/vim-plug/nvim/plugins.vim`
    
    ```
    " auto-install vim-plug
    " =============================================================================
    " Plugin Manager Setup
    " =============================================================================
    "
    filetype off
    
    " Install the plugin manager if it doesn't exist
    let s:plugin_manager=expand('~/.vim/autoload/plug.vim')
    let s:plugin_url='https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
    
    if empty(glob(s:plugin_manager))
      echom 'vim-plug not found. Installing...'
      if executable('curl')
        silent exec '!curl -fLo ' . s:plugin_manager . ' --create-dirs ' .
              \ s:plugin_url
      elseif executable('wget')
        call mkdir(fnamemodify(s:plugin_manager, ':h'), 'p')
        silent exec '!wget --force-directories --no-check-certificate -O ' .
              \ expand(s:plugin_manager) . ' ' . s:plugin_url
      else
        echom 'Could not download plugin manager. No plugins were installed.'
        finish
      endif
      augroup vimplug
        autocmd!
        autocmd VimEnter * PlugInstall
      augroup END
    endif
    
    call plug#begin('~/.config/nvim/autoload/plugged')
    
    call plug#end()
    ```
    
    [plugins.vim](Neovim%2070a57143355f4b24a491505bbcd27f11/plugins%201.vim)
    
- → `~/.config/nvim/autoload/plug.vim`
    
    [plug.vim](Neovim%2070a57143355f4b24a491505bbcd27f11/plug.vim)
    
- → `~/.config/nvim/init.vim`
    
    ```bash
    source ~/.config/nvim/settings.vim
    source ~/.config/nvim/keys/mappings.vim
    source ~/.config/nvim/vim-plug/plugins.vim
    source ~/.config/nvim/plug-config/telescope.vim
    ```
    
    [init.vim](Neovim%2070a57143355f4b24a491505bbcd27f11/init.vim)
    
- → `~/.config/nvim/keys/mappings.vim`
    
    ```bash
    " Better nav for omnicomplete
    inoremap <expr> <c-j> ("\<C-n>")
    inoremap <expr> <c-k> ("\<C-p>")
    
    " Use alt + hjkl to resize windows
    nnoremap <M-j>    :resize -2<CR>
    nnoremap <M-k>    :resize +2<CR>
    nnoremap <M-h>    :vertical resize -2<CR>
    nnoremap <M-l>    :vertical resize +2<CR>
    
    " Easy CAPS
    inoremap <c-u> <ESC>viwUi
    nnoremap <c-u> viwU<Esc>
    
    inoremap <C-s> <esc>:w<cr>                 " save files
    nnoremap <C-s> :w<cr>
    inoremap <C-d> <esc>:wq!<cr>               " save and exit
    nnoremap <C-d> :wq!<cr>
    inoremap <C-q> <esc>:exit<cr>               " quit discarding changes
    nnoremap <C-q> :exit<cr>
    
    inoremap ;; <Esc>
    
    " Better tabbing
    vnoremap < <gv
    vnoremap > >gv
    
    " Better window navigation
    nnoremap <C-h> <C-w>h
    nnoremap <C-j> <C-w>j
    nnoremap <C-k> <C-w>k
    nnoremap <C-l> <C-w>l
    
    nnoremap <Leader>o o<Esc>^Da
    nnoremap <Leader>O O<Esc>^Da 
    
    " Open nerdTree with keyshortcut
    let mapleader = ","
    nmap <leader>ne :NERDTree<cr>
    
    " TABS
    noremap <Tab> :tabnext<CR>
    noremap <S-Tab> :tabprevious<CR>
    nnoremap <C-t> :tabnew <bar> :NERDTree<CR>
    noremap <C-e> :tabclose<CR>
    
    " No more Arrow keys, deal with it
    noremap <Up> <NOP>
    noremap <Down> <NOP>
    noremap <Left> <NOP>
    noremap <Right> <NOP>
    noremap <S>k <NOP>
    
    tnoremap ;; <C-\><C-n>
    
    " Opens a new terminal in vertical split
    noremap <Leader>t :vsplit term://zsh<CR>
    
    " Comment lines
    noremap <Leader>cc 
    
    "Search for all ocourrences of the phrase that you write
    nnoremap <C-f> :lua require('telescope.builtin').grep_string({ search = vim.fn.input("Grep For > ") })<CR>
    
    " CTRL + C now yank the selected
    vmap <C-C> "+y
    
    " Clears the vim highlighing
    noremap <C-l> :noh<CR>
    
    " Changes all ocourrences for the text that you have typed
    nnoremap <Leader>r :%s///g<Left><Left>
    nnoremap <Leader>rc :%s///gc<Left><Left><Left>
    
    xnoremap <Leader>r :s///g<Left><Left>
    xnoremap <Leader>rc :s///gc<Left><Left><Left>
    
    vnoremap * y/\V<C-R>=escape(@",'/\')<CR><CR>
    
    "Debugging keys
    nnoremap <Leader>dd :call vimspector#Launch()<CR>
    nnoremap <Leader>de :call vimspector#Reset()<CR>
    nnoremap <Leader>dc :call vimspector#Continue()<CR>
    
    nnoremap <Leader>dt :call vimspector#ToggleBreakpoint()<CR>
    nnoremap <Leader>dT :call vimspector#ClearBreakpoints()<CR>
    
    nmap <Leader>dk <Plug>VimspectorRestart
    nmap <Leader>dh <Plug>VimspectorStepOut
    nmap <Leader>dl <Plug>VimspectorStepInto
    nmap <Leader>dj <Plug>VimspectorStepOver
    
    " Keys for completion
    inoremap <silent><expr> <C-Space> compe#complete()
    inoremap <silent><expr> <C-e>     compe#close('<C-e>')
    ```
    

---

- https://github.com/junegunn/vim-plug
- https://github.com/preservim/nerdtree
- https://github.com/dracula/dracula-theme
- https://github.com/tpope/vim-fugitive
- https://github.com/junegunn/fzf.vim
- https://github.com/fatih/vim-go
- https://github.com/vim-airline/vim-airline

## Fonts

1. Download 
2. Unzip
3. `cp *.tff ~/.fonts`  

[GitHub - ryanoasis/nerd-fonts: Iconic font aggregator, collection, & patcher. 3,600+ icons, 50+ patched fonts: Hack, Source Code Pro, more. Glyph collections: Font Awesome, Material Design Icons, Octicons, & more](https://github.com/ryanoasis/nerd-fonts#option-3-install-script)

[GitHub - microsoft/cascadia-code: This is a fun, new monospaced font that includes programming ligatures and is designed to enhance the modern look and feel of the Windows Terminal.](https://github.com/microsoft/cascadia-code)

[](https://linuxconfig.org/how-to-install-fonts-on-ubuntu-22-04-jammy-jellyfish-linux)

## Resolvendo warnings

→ dentro do `nvim` → `:checkhealth`

→ Resolvendo warning de `clipboard` → [https://stackoverflow.com/questions/67598285/cannot-paste-from-clipboard-in-neovim-nightl](https://stackoverflow.com/questions/67598285/cannot-paste-from-clipboard-in-neovim-nightly)a

→ Resolvendo warning de `ruby` → [https://linuxhint.com/ways-install-ruby-ubuntu/](https://linuxhint.com/ways-install-ruby-ubuntu/)

### Ruby

```bash
sudo apt install git curl autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm6 libgdbm-dev libdb-dev

curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash
```

Path

```bash
# Ruby
export PATH=$PATH:~/.rbenv/bin:~/.rbenv/shims
eval $(rbenv init -)
```

Install

```bash
rbenv install 3.1.2

rbenv global 3.1.2
```

## Referências

[optimizing your workflow with fzf & ripgrep](https://dev.to/hayden/optimizing-your-workflow-with-fzf-ripgrep-2eai)

[Configuring NeoVim plugins](https://dev.to/killerasus/configuring-neovim-plugins-2kj0)

[Instalando e configurando NVIM do ZERO no Linux e Windows - Configurando NVIM do Zero | Parte 1](https://youtu.be/YBPL3AfXU2M)

[Configuração VIM para programação backend #vim #neovim](https://youtu.be/N68nyJcVTE8)

[FABIO CARNEIRO: NEOVIM - CONFIGURAÇÃO E PLUGINS](https://youtu.be/A2pVyXi6g2Q)

[Learn VIM while playing a game - VIM Adventures](https://vim-adventures.com/)

[Trending dark vim color schemes | vimcolorschemes](https://vimcolorschemes.com/dark/)

[My Vim IDE setup for Go.](https://tpaschalis.github.io/vim-go-setup/)

[GitHub - vim-airline/vim-airline-themes: A collection of themes for vim-airline](https://github.com/vim-airline/vim-airline-themes#vim-airline-themes--)
