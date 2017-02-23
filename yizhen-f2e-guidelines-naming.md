# 命名规范

## 项目命名
全部采用小写方式，以分隔符 `-` 连接，沿用现有的项目命名方式。例如：my-project-jack

## 目录、文件命名
全部采用小写方式，以分隔符 `_` 连接，有复数结构时，要采用复数命名法。

例如：pages, images 目录名称；index_detail.html, plguin.js, sprite_index.scss 文件名称。

## 特别说明
1. scss 文件中，不需要单独编译的文件都必须采用这种名称方式，然后 import 到最终的出口文件里。

    ```
    scss/
    ├── style.scss
    ├── pages/
    │   ├── _list_item.scss
    │   └── _list_detail.scss
    ├── layout/
    │   ├── _rightnav.scss
    │   └── _topbar.scss
    └── base/
        └── _iconfont.scss
    ```
    
2. html 文件中，也会出现公共模块页面，采用 include 的方式，在其余页面中调用。
    TODO 这里是否也可以沿用 scss 的文件结构和命名方式，非直接编辑的独立文件和目录，都以 `_` 开头。

    ```
    pages/
    ├── _includes/
    │   ├── footer.html
    │   └── header.html
    ├── history_compare.html
    ├── history_list.html
    └── ...
    ```