# 编辑器配置

## 插件安装

1. SCSS-Lint - [https://github.com/brigade/scss-lint](https://github.com/brigade/scss-lint) `gem install scss_lint`
2. CSScomb - [https://github.com/csscomb/csscomb.js](https://github.com/csscomb/csscomb.js) `npm install csscomb -g`

---

## 配置文件  
会集中放进这个 gist 里，[Yizhen-F2E Editor Preferences](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402)

1. EditorConfig - [.editorconfig](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402#file-editorconfig)
2. CSScomb - [.csscomb.json](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402#file-csscomb-json)
3. SCSS-Lint - [.scss-lint.yml](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402#file-scss-lint-yml)

---

## 编辑器设置

1. IntelliJ IDEA

相关个性化的设置，个人根据喜好去配置即可。
EditorConfig 配置文件导入到项目根目录下，不过一般公共配置文件会提交到项目中，如果 checkout 的项目中没有发现此配置文件，可以自主下载。

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
    - TODO：但是实际使用情况，并非 repo 里描述的那样，在 win 里没能完成正确配置，有待继续跟进。同时也尝试了其余的 jetbrains plugins 目前还没有搜到更合适的，需要注意的是这里产出的 scss 源码最好也是符合各属性的声明顺序。