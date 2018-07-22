# creditchain
## 配置开发环境

安装express开发工具

    sudo npm install express-generator -g

检查有无安装成功

    express --help

进入自己的目录，创建websample

    cd ~
    mkdir websample

使用 ejs 模板库，创建一个名为 creditchain 的项目，并且不使用 CSS样式表引擎。

    cd websample
    express credit --view=ejs
    
