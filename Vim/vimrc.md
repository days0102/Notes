<!--
 * @Author: Outsider
 * @Date: 2022-01-22 21:15:03
 * @LastEditors: Outsider
 * @LastEditTime: 2022-01-22 21:17:21
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Vim\vimrc.md
-->

# vimrc文件的配置文件

## 基本配置
```VIM
"保存.vimrc文件时自动重启加载，即让此文件立即生效
autocmd BufWritePost $MYVIMRC source $MYVIMRC

""设置编码
"set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936
"set termencoding=utf-8
"set encoding=utf-8

"设置ruler会在右下角显示光标所在的行号和列号,不方便查看,改成设置状态栏显示内容
""set ruler

"设置状态行显示的内容. %F: 显示当前文件的完整路径. %r: 如果readonly,会显示[RO]
""%B: 显示光标下字符的编码值,十六进制. %l:光标所在的行号.
"%v:光标所在的虚拟列号.
"%P: 显示当前内容在整个文件中的百分比. %H和%M是strftime()函数的参数,获取时间.
"set statusline=%F%r\ [HEX=%B][%l,%v,%P]\ %{strftime(\"%H:%M\")}

"突出显示当前行
"set cursorline   "等同于 set cul

"突出显示当前列
"set cursorcolumn "等同于 set cuc

"共享剪贴板
"set clipboard+=unnamed
"
""从不备份
"set nobackup

"自动保存
"set autowrite
"
""隐藏工具栏
"set guioptions-=T
""隐藏菜单栏
"set guioptions-=m
"
""高亮显示所有搜索到的内容.后面用map映射快捷键来方便关闭当前搜索的高亮.
"set hlsearch
"
""光标立刻跳转到搜索到内容
"set incsearch
"
""搜索到最后匹配的位置后,再次搜索不回到第一个匹配处
"set nowrapscan
"
""去掉输入错误时的提示声音
"set noeb

" 默认按下Esc后,需要等待1秒才生效,设置Esc超时时间为100ms,尽快生效
" set ttimeout
" set ttimeoutlen=100
"
" "在处理未保存或只读文件的时候，弹出确认
" set confirm
"
" "让Backspace键可以往前删除字符.
" "Debian系统自带的vim版本会加载一个debian.vim文件,默认已经设置这一项,
" "可以正常使用Backspace键.如果使用自己编译的vim版本,并自行配置.vimrc文件,
" "可能就没有设置这一项,导致Backspace键用不了,或者时灵时不灵.所以主动配置.

"使回格键（backspace）正常处理indent, eol, start等
" set backspace=indent,eol,start
"
" "允许backspace和光标键跨越行边界
" "set whichwrap+=<,>,h,l
"
" "去掉有关vi一致性模式,避免操作习惯上的局限.
" set nocompatible

" "FIXME 在MS-DOS控制台打开vim时,控制台使用鼠标右键来复制粘贴,设置
" "全鼠标模式,鼠标右键被映射为visual mode,不能用来复制粘贴,不方便.
" "但是如果不设置鼠标模式,会无法使用鼠标滚轮来滚动界面.经过验证,发现
" "可以设成普通模式mouse=n来使用鼠标滚轮,也能使用鼠标右键复制粘贴.
" " mouse=c/mouse=i模式都不能用鼠标滚轮. Linux下还是要设成 mouse=a
"set mouse=n
"set selection=exclusive
"set selectmode=mouse,key

"高亮显示括号匹配
set showmatch

" "设置Tab长度为4空格
" set tabstop=4
" "设置自动缩进长度为4空格
" set shiftwidth=4
" "自动缩进,这个导致从外面拷贝多行以空格开头的内容时,会有多的缩进,先不设置
" "set autoindent
" "不要用空格代替制表符
" set noexpandtab
" "输入tab制表符时，自动替换成空格
" "set expandtab
" "设置softtabstop有一个好处是可以用Backspace键来一次删除4个空格.
" "softtabstop的值为负数,会使用shiftwidth的值,两者保持一致,方便统一缩进.
" "set softtabstop=4


" "显示空格和tab键
" set listchars=tab:>-,trail:-

"1=启动显示状态行, 2=总是显示状态行.设置总是显示状态行,方便看到当前文件名
set laststatus=2


"语法高亮
syntax on

set nu  "显示行号

set ts=4              "ts为tabstop缩写，设tab宽度为4个空格
set softtabstop=4 "退格键删除4个空格
set shiftwidth=4  "每一格缩进的长度，一般设置和softtabstop相同
set expandtab     "缩进用空格表示，noexxpandtab表示用制表符表示缩进
set autoindent    "自动缩进
```

## 键盘映射