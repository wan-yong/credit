# export书写规范

## 导出多个
### 方法1：module.前缀，随时可以加
```
exuser.js
module.exports.a = function () {
  console.log('a exports');
}
 
module.exports.b = function () {
  console.log('b exports');
}
```
### 方法2：
左外右內的键值对
```
module.exports = {
    greet: greet,
    hi: hi,
};

function greet(name) {
    console.log('Hello' + ', ' + name + '!');
}

function hi(name) {
    console.log('Hi, ' + name + '!');
}

function goodbye(name) {
    console.log('Goodbye, ' + name + '!');
}
```
使用：
```
use.js
var useExports = require('./exuser');
useExports.a();
useExports.b();
```
## 导出单个
### 方法1：
    exports.hello = fun(){};

### 方法2：
```
var person = {
          hello : fun(){};
    };
    module.exports = person;
```
使用：app.js
```
var person = require(‘person’);
person.hello();
```
## 匿名方法
### 方法1：
sayWorld.js
```
module.exports = function () {
    console.log('world');
}
```
### 方法2：
sayWorld.js
```
var sayWorld' = fun(){
   console.log('world');
};
module.exports = sayWorld';
```
使用：app.js
```
var sayWorld = require('./sayWorld');
sayWorld(); //匿名函数，直接加个()
```
## 构造用法
```
var Person = require('./person');
var person = new Person('Jane');
person.hello();

//调用的模块，仅最后一段不同
function Person(name) {
     this.name = name;
}

Person.prototype.hello = function() {
     console.log("Hi, I'm " + this.name);
};

module.exports = Person;
```
## 工厂用法
```
var Person = require('./person');
var person = Person('Jane');
person.hello();

//调用的模块，仅最后一段不同

module.exports = function(name){
    return new Person(name);
};
```
## 模块的依赖关系用__filename
    module.exports = require('./models')(__filename);

## npm安装的第三方模块
```
var nav=require('nav');  //引入 npm安装的模块。此时nav表示文件夹，而不是nav.js。 npm安装模块：进入模块所在的目录运行命令（cmd环境） npm init --yes 。 会在目录下生成package.json文件 
//nav 在默认目录下不存在，会去node_modules，找到了nav文件夹。 nav文件夹下面有package.json ，找 package.json 入口文件 "main": "123.js"
// -->node_modules-->nav文件夹-->package.json-->入口文件 "main": "123.js" -->123.js
console.log(nav.str);
//var nav=require('nav/123.js');  //相当于这样引入
```
## 参考资料
    https://blog.csdn.net/j_y_x_8/article/details/52045716
    https://github.com/WhiteYin/translation/issues/2
