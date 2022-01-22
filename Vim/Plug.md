<!--
 * @Author: Outsider
 * @Date: 2022-01-21 21:02:47
 * @LastEditors: Outsider
 * @LastEditTime: 2022-01-21 22:02:41
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Vim\Plug.md
-->


# Plug插件使用
- curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

- .vimrc配置
```
call plug#begin()

[插件]

call plug#end()
```

## coc代码自动补全
1. Install nodejs >= 12.12:
```
curl -sL install-node.vercel.app/lts | bash
```
2. For vim-plug users:
```
" Use release branch (recommend)
Plug 'neoclide/coc.nvim', {'branch': 'release'}

" Or build from source code by using yarn: https://yarnpkg.com
Plug 'neoclide/coc.nvim', {'branch': 'master', 'do': 'yarn install --frozen-lockfile'}
```