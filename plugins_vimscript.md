
```vim
"
" ----------------------------------------
" PLUGIN configuration
" ----------------------------------------
"

" code DARK
colorscheme codedark

" IndentLines
map <c-k>i :IndentLinesToggle<CR>

" --
let php_special_vars = 0
let g:tabular_loaded = 1

" set the names of flags
let tlist_php_settings = 'php;c:class;f:function;d:constant'

" close all folds except for current file
let Tlist_File_Fold_Auto_Close = 1

" make tlist pane active when opened
let Tlist_GainFocus_On_ToggleOpen = 1

" width of window
let Tlist_WinWidth = 40

" close tlist when a selection is made
let Tlist_Close_On_Select = 1

" 
" OmniCppComplete
" ----------------------------------------
"
let OmniCpp_NamespaceSearch = 1
let OmniCpp_GlobalScopeSearch = 1
let OmniCpp_ShowAccess = 1
let OmniCpp_ShowPrototypeInAbbr = 1 " show function parameters
let OmniCpp_MayCompleteDot = 1 " autocomplete after .
let OmniCpp_MayCompleteArrow = 1 " autocomplete after ->
let OmniCpp_MayCompleteScope = 1 " autocomplete after ::
let OmniCpp_DefaultNamespaces = ["std", "_GLIBCXX_STD"]

let g:acp_ignorecaseOption = 0 " ignore Case 0|1
let g:acp_enableAtStartup = 0 " auto popup 0|1

inoremap <Leader>e <C-O>:call PhpExpandClass()<CR>
inoremap <Leader>u <C-O>:call PhpInsertUse()<CR>
inoremap <Leader>i <C-O>:call PhpImplement()<CR>

"autocmd BufRead *.* norm zR
"autocmd BufRead,BufNewFile *.php set filetype=php.rubricate
"autocmd FileType php  set tags^=~/www/tags/framework/rubricate

" 
" config syntax html5
" ----------------------------------------
"
let g:html5_event_handler_attributes_complete = 0 " Disable event-handler attributes support:
let g:html5_rdfa_attributes_complete = 0 " Disable RDFa attributes support:
let g:html5_microdata_attributes_complete = 0 " Disable microdata attributes support:
let g:html5_aria_attributes_complete = 0 " Disable WAI-ARIA attribute support:

" 
" ctags PHP
" ---------------------------------------- 
"
" map <C-F12> :!ctags -R --sort=yes --c++-kinds=+p --fields=+iaS --extra=+q .<CR>
noremap <leader>4 :!ctags -R 
            \--recurse=yes --tag-relative=yes 
            \--exclude=.git --exclude=*.vim 
            \--PHP-kinds=+cfi --fields=+aimlS 
            \--exclude=composer.phar 
            \--exclude=*Test.php 
            \--exclude=*phpunit* 
            \--languages=php .<CR>

let php_sql_query=1
let php_htmlInStrings=1

let g:phpcomplete_relax_static_constraint = 1
let g:phpcomplete_enhance_jump_to_definition = 1
let g:phpcomplete_add_class_extensions = ['mongo']
let g:phpcomplete_add_function_extensions = ['mongo']
let g:phpcomplete_cache_taglists = 1
let g:phpcomplete_min_num_of_chars_for_namespace_completion = 1
let g:phpcomplete_remove_function_extensions = ['xslt_php_4']
let g:phpcomplete_remove_constant_extensions = ['xslt_php_4']

" 
" FuzzyFinder
" ----------------------------------------
"
let g:fuf_modesDisable = []
let g:fuf_mrufile_maxItem = 1000
let g:fuf_mrucmd_maxItem = 400

map ,f :FufFile<cr>
map ,b :FufBuffer<cr>
map ,t :FufTag<cr>

" 
" show/hide the NERDTree
" ----------------------------------------
"
cab ntree NERDTreeToggle|cab NTREE NERDTreeToggle
cab Ntree NERDTreeToggle|cab nTREE NERDTreeToggle
cab nerdTree NERDTreeToggle|cab NERDTREE NERDTreeToggle
cab nerdtree NERDTreeToggle
cab ntreeo NERDTree|cab ntreec NERDTreeClose
cab ntreeopen NERDTree|cab ntreeclose NERDTreeClose
map <leader>n :NERDTreeToggle<CR>

" TComment
cab tcomment TComment

" 
" ctrlP
" ----------------------------------------
"
let g:ctrlp_custom_ignore = '\v[\/]\.(git|hg|svn)$'
let g:ctrlp_custom_ignore = {
  \ 'dir':  '\v[\/]\.(git|hg|svn)$',
  \ 'file': '\v\.(exe|so|dll)$',
  \ 'link': 'some_bad_symbolic_links',
  \ }


" VIMScripts

function! DebugLineNumber()

    let ln = line('.') + 1
    let str_fmt = "\\App\\Infra\\Logger\\FileLogger::debug('ln%d', '');"

    call append(line('.'), printf(str_fmt, ln))
    call cursor(ln, 1)
    normal! f)h

endfunction

function! EchoLineNumber()

    let ln = line('.') + 1
    let str_fmt = "echo 'ln%d<br />' . PHP_EOL;"
    call append(line('.'), printf(str_fmt, ln))
    call cursor(ln, 1)

endfunction

map ,d :call DebugLineNumber()<cr>
map ,l :call EchoLineNumber()<cr>

```
