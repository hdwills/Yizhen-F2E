# 编辑器配置

## 插件安装

1. SCSS-Lint - [https://github.com/brigade/scss-lint](https://github.com/brigade/scss-lint) `gem install scss_lint`
2. CSScomb - [https://github.com/csscomb/csscomb.js](https://github.com/csscomb/csscomb.js) `npm install csscomb -g`

## 配置文件  
会集中放进这个 gist 里，[Yizhen-F2E Editor Preferences](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402)

1. EditorConfig - [.editorconfig](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402#file-editorconfig)
2. CSScomb - [.csscomb.json](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402#file-csscomb-json)
3. SCSS-Lint - [.scss-lint.yml](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402#file-scss-lint-yml)

## 编辑器设置

相关个性化的设置，个人根据喜好去配置即可。  
其余相关的规范文件，都以文档为主，去逐一配置。推荐 [JetBrarins](https://www.jetbrains.com/) 旗下的 IDE 或者 [Sublime Text](https://www.sublimetext.com/)。

### IntelliJ IDEA

* scss-lint：
    - [https://github.com/idok/scss-lint-plugin](https://github.com/idok/scss-lint-plugin)
    - 可以通过上面提供的链接，自己去找下载后本地安装。
    - 可以去编辑器的仓库里在线安装，再进行设置。
    - 配置文件也需要与项目同步

    ![IDE Settings](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_scsslint_111548.png)

    ![Configuration](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_scsslint_145214.png)

    ![Inspection](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_scsslint_150505.png)

    ![Analyze Code](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_scsslint_151223.png)

* csscomb：
    - jetbrains-csscomb - [https://github.com/csscomb/jetbrains-csscomb](https://github.com/csscomb/jetbrains-csscomb)
    - TODO：但是实际使用情况，并非 repo 里描述的那样，在 win 里没能完成正确配置，有待继续跟进。同时也尝试了其余的 jetbrains plugins 目前还没有搜到更合适的，需要注意的是这里产出的 scss 源码最好也是符合各属性的声明顺序，即使我们最终会用工具去统一输出。

### Sublime Text 3

* Sublime Text Package Control - [https://packagecontrol.io/installation](https://packagecontrol.io/installation)。在编辑器中按下快捷键 `Ctrl + ``，从上面的地址中粘贴对应的代码到编辑器里，回车执行。这些代码回创建对应的目录了相应的依赖包等。
* 安装插件
    `ctrl+shift+p`，输入 `ip`。简写的命令(Package Control: Install Package)。看左下角的 loading 状态，等插件目录加载完成后会显示出插件列表，再逐一安装以下插件：
    + EditorConfig
    + Sass
    + SublimeLinter
    + SublimeLinter-contrib-scss-lint
    + CSScomb
* 实际使用效果
    安装完以上的插件之后，就可以看看实际使用效果了。支持 `*.scss` 语法高亮，SCSS-Lint 也已经生效，见下图 1（代码行处的图标提示，光标定位到当前行之后，底部的状态栏有对应的修正提示）；CSScomb 使用效果见下图2。

    ![SCSS-Lint](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_st3_150724.png)

    ![CSScomb](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_st3_150240.gif)
