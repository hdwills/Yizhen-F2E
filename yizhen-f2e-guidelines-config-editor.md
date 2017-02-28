# 编辑器配置
## IntelliJ IDEA
1. 编辑器设置

    相关个性化的设置，个人根据喜好去配置即可。  
    1. EditorConfig 配置文件导入到项目根目录下，不过一般公共配置文件会提交到项目中，如果 checkout 的项目中没有发现此配置文件，可以自主下载。

2. 插件安装
    1. scss-lint

        * 插件安装、配置：
            - [https://github.com/brigade/scss-lint](https://github.com/brigade/scss-lint)
                ``` ruby
                gem install scss_lint
                ```
            - [https://github.com/idok/scss-lint-plugin](https://github.com/idok/scss-lint-plugin)
            - 可以通过上面提供的链接，自己去找下载后本地安装。
            - 可以去编辑器的仓库里在线安装，再进行设置。
        
        * 插件使用：
            ![IDE Settings](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_scsslint_111548.png)

            ![Configuration](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_scsslint_145214.png)

            ![Inspection](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_scsslint_150505.png)

            ![Analyze Code](https://raw.githubusercontent.com/hdwills/Yizhen-F2E/master/assets/images/edc_scsslint_151223.png)

3. 配置文件  
    会集中放进这个 gist 里，[Yizhen-F2E Editor Preferences](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402)
    1. EditorConfig - [.editorconfig](https://gist.github.com/hdwills/9cfb8654d653b616dbc824a90222f402#file-editorconfig)