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
    
安装依赖包

    cd credit && npm install
    npm install --save body-parser
    npm install --save serve-favicon
       
让服务器在文件更改时，自动重新启动

    npm install --save-dev nodemon

修改package.json 的脚本 scripts 区块，找到以"start"开头的代码段，在该行的末尾添加逗号，然后，添加"devstart" 开头的一行

    "scripts": {
    "start": "node ./bin/www",
    "devstart": "nodemon ./bin/www"
    },
    
启动服务器

    DEBUG=credit:* npm run devstart
    
现在，如果编辑项目中的任何文件，服务器自动重新启动。刷新浏览器，就能看到程序的调试结果。

下载源码到本地进行调试

    git clone https://github.com/wan-yong/credit.git
    cd credit
    
##备注

    http://www.cnblogs.com/best/p/6204116.html#_label0
    https://www.bilibili.com/video/av17977069/
    https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/Express_Nodejs/routes
