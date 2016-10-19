# MIP 扩展组件规范

## 目录结构

以sample组件为例：
mip-extensions
    - mip-sample
        - mip-sample.js
        - mip-sample.less
        - package.json
        - READMD.md

注：其中 package.json READMD.md mip-sample.js 为必要文件，mip-sample.less 为可选文件，是否选用以具体组件为准。


## package.json 规范

示例：  
```json
{
    "name": "mip-sample",
    "version": "1.0.1",
    "contributors": [
        {
            "name": "author",
            "email": "author@xxx.com"
        } 
    ],
    "engines": {
        "mip": "1.0.0"
    }
}
```

### 字段说明

#### name

描述：组件名  
必填：是

#### version

描述：三位版本号。第一位表示组件大版本，第二位表示组件功能，第三位为BUG修复。每次push代码都必须升版本号。
必填：是  
取值：以1.0.0为起始版本  


#### contributors

描述：代码贡献者  
必填：是  

## README.md 规范

格式：  
```
#[组件名]

[组件描述]

标题|内容
----|----
类型|[见注2:类型说明]
支持布局|[见注3：布局说明]
所需脚本|[代码上线后的地址]

## 示例

### [如果有多个示例，以###为标题，如果没有可不填]

[示例介绍]  

```html
[<p>Html code</p>]
```

## 属性

### [属性名]

说明|[文字描述，说明属性用途]
必填|[是或否]
格式|[属性格式 数字，字符串等，如属性是 10px 类型，那么格式应该是 数字+单位]
取值|[取值表示属性的取值范围，可选，如果是泛数字类型，应该用数学符号表示，如 > 10 或者 > 10px。如果是
限定类型的取值可用","隔开。如 left,top,right,down，表示任选其一]
单位|[属性的单位，可选。如果属性可以用多个单位，可用","隔开，如 px,em,pt,rem]
默认值|[如果有默认值，可选用此字段，非必填]
使用限制|[文字描述，说明属性的使用限制，可选]


[属性说明字段]:[字段内容](见注4：属性说明字段)

## 注意事项

### [注意事项标题，如果只有一条，此标题可省略]

[具体描述]
```

注：  
1、其中"[]"意味着需要开发者手动添写。如开发了mip-demo组件，那么"[标题]"需要替换成"mip-demo"
2、类型说明：组件应注明属于哪种类型。我们定义了几种组件类型，组件的类型可以是一个也可以是多个，多个类型以","分隔。如果需要增加其它类型，可与我们联系。
    - 通用：表示组件是通用的组件，组件定位是所有网站可用  
    - 业务：即所开发网站的业务组件，不具有通用性
    - 广告：广告组件  
    - 定制：针对某个网站或某种业务的组件，具有一定通用性，如视频网站的播放组件

以优酷视频播放组件为例，它的类型应该是：通用,定制  
3、布局说明：布局应在官网提供的布局中选用几种。具体布局介绍见官网[组件布局](https://www.mipengine.org/doc/4-widget/1-widgetlayout.html)  
4、属性说明字段：属性说明字段用于说明一个属性应该怎样使用，有什么限制等。格式为 "字段名：字段内容"。字段应该在下面几种里选用
4、在 "##" 的二级标题中，"示例" 是必选项，"属性" 在组件需要加属性的情况下也是必填字段，"注意事项" 表示附加说明，可选用。二级标题暂只可用这三种，如果需要增加其它标题，可以联系我们增加。

### 示例

请见 mip-sample 的[READMD.md](https://github.com/mipengine/mip-extensions/blob/master/mip-sample/README.md)

## js 规范

组件的主文件应与组件同名，如mip-sample的主文件是mip-sample.js。  
统一使用 amd 模块化开发

### 文件命名方式

统一使用小写字母，以中横线 "-" 做为连结符。

### 文件格式
```
define(function (require) {
    // Code
});

```

### 同步引入模块

在组件目录下创建 [模块名].js，在主文件中
```
define(function (require) {
    var demo = require('./demo');
});
```

### 异步引入模块

在组件目录下创建 [模块名].js，在主文件中
```
define(function (require) {
    require(['./demo'], function () {
        // Code
    });
});
```

### 开发文档
见[扩展组件开发手册](https://github.com/mipengine/mip-plugins/tree/master/extensions)

## css 规范

css 统一使用 less，以 [组件名].less 做为主文件。并且原则上不能出现 "a" "body" 这样的全局选择器。

