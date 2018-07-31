"""""""""""""""""""""""""""
"dein.vim
"""""""""""""""""""""""""""
if &compatible
 set nocompatible
endif
" Add the dein installation directory into runtimepath
set runtimepath+=~/.cache/dein/repos/github.com/Shougo/dein.vim
let s:dein_dir = expand('~/.cache/dein')

if dein#load_state(s:dein_dir)
call dein#begin(s:dein_dir)

call dein#load_toml(s:dein_dir . '/plugins.toml', {'lazy': 0})
call dein#add('Shougo/deoplete.nvim')
if !has('nvim')
  call dein#add('roxma/nvim-yarp')
  call dein#add('roxma/vim-hug-neovim-rpc')
endif

call dein#end()
call dein#save_state()
endif

if dein#check_install()
 call dein#install()
endif

filetype plugin indent on
syntax enable

"colorschemeの設定
"set t_Co=256
" set background=dark
"colorscheme molokai



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"   起動時実行
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

augroup start
augroup end


"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"   Plugins
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

"airlineの設定
colorscheme solarized
let g:airline_solarized_bg='dark'
let g:solarized_termcolors=256
" set guifont=Roboto_Mono_for_Powerline:h14
set laststatus=2
" let g:airline_powerline_fonts = 1
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#buffer_idx_mode = 1
let g:airline#extensions#whitespace#mixed_indent_algo = 1
let g:airline_theme='luna'

let g:indent_guides_enable_on_vim_startup = 0
let g:indent_guides_auto_colors = 0
" 奇数インデントのカラー
"autocmd VimEnter,Colorscheme * :hi IndentGuidesOdd  guibg=#262626 ctermbg=gray
" 偶数インデントのカラー
"autocmd VimEnter,Colorscheme * :hi IndentGuidesEven guibg=#3c3c3c ctermbg=darkgray

"python用の設定
autocmd FileType python set sw=4
autocmd FileType python set ts=4
autocmd FileType python set sts=4

"Syntasticの設定
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*
let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 0
let g:syntastic_check_on_wq = 0
let g:syntastic_python_checkers = ["flake8"]
"django推奨設定
let g:last_relative_dir = ''
nnoremap \1 :call RelatedFile ("models.py")<cr>
nnoremap \2 :call RelatedFile ("views.py")<cr>
nnoremap \3 :call RelatedFile ("urls.py")<cr>
nnoremap \4 :call RelatedFile ("admin.py")<cr>
nnoremap \5 :call RelatedFile ("tests.py")<cr>
nnoremap \6 :call RelatedFile ( "templates/" )<cr>
nnoremap \7 :call RelatedFile ( "templatetags/" )<cr>
nnoremap \8 :call RelatedFile ( "management/" )<cr>
nnoremap \0 :e settings.py<cr>
nnoremap \9 :e urls.py<cr>

fun! RelatedFile(file)
    #This is to check that the directory looks djangoish
    if filereadable(expand("%:h"). '/models.py') || isdirectory(expand("%:h") . "/templatetags/")
        exec "edit %:h/" . a:file
        let g:last_relative_dir = expand("%:h") . '/'
        return ''
    endif
    if g:last_relative_dir != ''
        exec "edit " . g:last_relative_dir . a:file
        return ''
    endif
    echo "Cant determine where relative file is : " . a:file
    return ''
endfun

fun SetAppDir()
    if filereadable(expand("%:h"). '/models.py') || isdirectory(expand("%:h") . "/templatetags/")
        let g:last_relative_dir = expand("%:h") . '/'
        return ''
    endif
endfun
autocmd BufEnter *.py call SetAppDir()

"YouCompleteMe用の設定
let g:ycm_keep_logfiles = 1
let g:ycm_log_level = 'debug'
let g:ycm_global_ycm_extra_conf = '$USER/.cache/dein/repos/github.com/valloric/youcompleteme/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py'
"django推奨設定
let g:ycm_collect_identifiers_from_tags_files = 1 " Let YCM read tags from Ctags file
let g:ycm_use_ultisnips_completer = 1 " Default 1, just ensure
let g:ycm_seed_identifiers_with_syntax = 1 " Completion for programming language's keyword
let g:ycm_complete_in_comments = 1 " Completion in comments
let g:ycm_complete_in_strings = 1 " Completion in string

"Ultisnips.vim用の設定
let g:UltiSnipsExpandTrigger       = "<c-j>"
let g:UltiSnipsJumpForwardTrigger  = "<c-j>"
let g:UltiSnipsJumpBackwardTrigger = "<c-p>"
let g:UltiSnipsListSnippets        = "<c-k>" "List possible snippets based on current file

"Surround用の設定
let b:surround_{char2nr("v")} = "{{ \r }}"
let b:surround_{char2nr("{")} = "{{ \r }}"
let b:surround_{char2nr("%")} = "{% \r %}"
let b:surround_{char2nr("b")} = "{% block \1block name: \1 %}\r{% endblock \1\1 %}"
let b:surround_{char2nr("i")} = "{% if \1condition: \1 %}\r{% endif %}"
let b:surround_{char2nr("w")} = "{% with \1with: \1 %}\r{% endwith %}"
let b:surround_{char2nr("f")} = "{% for \1for loop: \1 %}\r{% endfor %}"
let b:surround_{char2nr("c")} = "{% comment %}\r{% endcomment %}"

"NERDCommenterの設定
let g:NERDSpaceDelims=1

"NERDTreeの設定
let NERDTreeShowHidden = 1

"flak8の設定


"行番号を表示
set number
"クリップボードの共有
set clipboard=unnamed,autoselect
"ファイル読み込み時の文字コードを指定
set enc=utf-8
"文字コードをutf-8に設定
set fenc=utf-8
"□や○文字が崩れる問題を解決
set ambiwidth=double
"バックアップファイルを作らない
set nobackup
"スワップファイルを作らない
set noswapfile
"編集中のファイルが変更されたら自動で読み直す
set autoread
"バッファが編集中でも他のファイルが開ける
set hidden
"入力中のコマンドをステータスに表示する
set showcmd

"行番号を表示
set number
"行にアンダーラインを表示
set cursorline
"行末の一つ先までカーソル移動できるようにする
set virtualedit=onemore
"ステータスラインを表示
set laststatus=2
"括弧入力時に対応する括弧を表示
set showmatch
"コマンドラインの補完
set wildmenu wildmode=list:longest,full
"ビープ音を無効
set visualbell t_vb=
"エラーメッセージの表示時にビープ音を鳴らさない
set noerrorbells
"上下8行の視界を確保
set scrolloff=8
"左右スクロール時のの視界を確保
set sidescrolloff=16

"inoremap { {}<ESC>i
"inoremap ( ()<ESC>i
"inoremap " ""<ESC>i
"inoremap ' ''<ESC>i
"inoremap ` ``<ESC>i
"inoremap [ []<ESC>i
"ハイライトを削除
nmap <F8> :TagbarToggle<CR>
nmap <ESC><ESC> :nohlsearch<CR><ESC>
nnoremap j gj
nnoremap k gk
nnoremap <down> gj
nnoremap <up> gk
"inoremap {<ENTER> {}<LEFT><CR><ESC><S-o>
"inoremap (<ENTER> ()<LEFT><CR><ESC><S-o>
set backspace=indent,eol,start

"tab系
"TAB文字を半角スペースにする
set expandtab
"行頭TAB文字の表示幅
set tabstop=4
"連続した空白に対してタブキーやバックスペースでカーソルが移動する幅
set softtabstop=4
"自動インデントでずれる幅
set shiftwidth=4
""自動的にインデントする
set cindent

"検索系
"検索文字列が小文字の場合は大文字小文字を区別なく検索する
set ignorecase
"検索文字列に大文字が含まれている場合は区別して検索する
set smartcase
"検索文字入力時に順次対象文字列にヒットさせる
set incsearch
"検索時に最後まで行ったら最初に戻る
set wrapscan
"検索語をハイライト表示
set hlsearch

set whichwrap=b,s,h,l,<,>,[,]
"ファイルのパスをタイトルに表示
set title
" カーソルが何行目の何列目に置かれているかを表示する
set ruler

"マウスの有効化
if has('mouse')
    set mouse=a
    if has('mouse_sgr')
        set ttymouse=sgr
    elseif v:version > 703 || v:version is 703 && has('patch632')
        set ttymouse=sgr
    else
        set ttymouse=xterm2
    endif
endif
