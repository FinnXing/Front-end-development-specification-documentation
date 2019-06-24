
规范的制定是我们长期以来对工作的积累与沉淀的产物，帮助我们更快、更好、更高效的完成复杂、繁重、多样化的任务，制定规范的主要目的在于：降低每个组员介入项目的门槛成本；提高工作效率及协同开发的便捷性；高度统一的代码风格，提供一整套HTML、CSS、JS解决方案，来帮助开发人员快速做出高质量的符合要求的代码。
本文档如有不对或不合适的地方请随时提出，经讨论决定后可更改此文档。
## __基本原则__
*   __结构、样式、行为分离：__

    尽量确保文档和模板只包含HTML结构，样式放在样式表里，行为放在脚本里。

*   __缩进：__

    使用tab(4个空格宽度)进行缩进。

*   __编码：__

    统一只用UTF-8，在HTML文档中使用`<meta charset="utf-8" />`，CSS中首行使用`@charset "utf-8"`。

*   __小写：__
    
    所有HTM标签和属性必须小写，所有的样式名和规则必须小写。


*   __注释：__
    
    尽可能为代码写注释，使用统一注释模板（详见各详细规范内注释要求）

*   __文件命名：__

    文件和文件夹使用小写字母、数字和“-”（减号）连接符命名，如：current-weather.html；
    HTML对应的CSS和JS文件必须同HTML同名，以便于快速对应查找，如：current-weather.css，current-weather.js。
    
*   __省略外链资源 URL 协议部分__

    省略外部资源（图片及其它媒体资源）URL中的`http`/`https`协议，使URL成为相对地址，避免Mixed Content问题，减小文件字节数。如：`<script src="//static.weathercn.com/js/base.js"></script>`

##  __HTML规范__

尽量遵循HTML标准和语义，不要以牺牲实用性和性能为代价，任何时候都要尽量使用最少的标签并保持最小的复杂度。

1.  __文档类型__

    *   __统一使用HTML5的标准文档类型：`<!DOCTYPE html>`；__
    *   __在文档DOCTYPE申明之前，不允许加入任何非空字符；__
    *   __不允许添加`<meta>`标签强制改变文档模式。__

2.  __HEAD__

    *   __字符编码__

        以无BOM的utf-8编码作为文件格式；

        指定字符编码的 `meta` 必须是`head`的第一个直接子元素。
        ```
        <html>
            <head>
                <meta charset="utf-8">
            </head>
        </html>
        ```

    *   __IE兼容模式__

        优先使用最新版本的IE和Chrome内核

        `<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">`

    *   __SEO 优化__

        为保证SEO优化，需添加`title`、`keywords`、`description`、`author`。
        ```
        <head>
            <meta charset="utf-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
            <!-- SEO -->
            <title>Style Guide</title>
            <meta name="keywords" content="your keywords">
            <meta name="description" content="your description">
            <meta name="author" content="author,email address">
        </head>
        ```

    *   __viewport__

        由于网站主要适配移动端，需设置相应`viewport`
        ```
        <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
        ```

    *   __浏览器内核控制__

        设置双核浏览器的浏览模式为webkit
        ```
        <meta name="renderer" content="webkit">
        ```

    *   __禁止百度转码和提高网站权重__

        ```
         <meta http-equiv="Cache-Control" content="no-siteapp" />
         <meta name="baidu_union_verify" content="4adcaa98aa51ff551c76cb736e23009a">
        ```

    *   __favicon__

        在未指定 favicon 时，大多数浏览器会请求 Web Server 根目录下的 favicon.ico 。为了保证 favicon 可访问，避免404，必须遵循以下两种方法之一：在 Web Server 根目录放置 favicon.ico 文件，使用 link 指定 favicon；
        ```
        <link rel="shortcut icon" href="path/to/favicon.ico">
        ```

    *   __HEAD 模板__

        ```
        <!DOCTYPE html>
        <html lang="zh-cmn-Hans">
        <head>
            <meta charset="utf-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
            <title></title>
            <meta name="description" content="不超过150个字符">
            <meta name="keywords" content="">
            <meta name="author" content="name, email@gmail.com">

            <!-- 为移动设备添加 viewport -->
            <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">

            <meta http-equiv="Cache-Control" content="no-siteapp" />
            <meta name="baidu_union_verify" content="4adcaa98aa51ff551c76cb736e23009a">
            <link rel="shortcut icon" href="path/to/favicon.ico">
        </head>
        ```
3.  __基本语法__

    *   __标签__
        
        所有可选闭合标签必须闭合，自闭合标签无需闭合，
        >如：`<li></li>`、`<img src="...">`。

        标签名必须使用小写字母；

        标签使用必须符合标签嵌套规则；
        >`<a>`标签内严禁嵌套交互式元素：`<a>`、`<button>`、`<select>`等；

        >`<p>`标签内严禁嵌套块级元素。

        HTML标签的使用应该遵循标签的语义-标签语义化；

        标签的使用应尽量简洁，减少不必要的标签。

    *   __属性__

        属性名必须使用小写字母，属性值必须使用双引号包围；

        自定义属性建议以`xxx-`为前缀，推荐使用`data-`；

        HTML属性应按照特定的顺序出现以保证阅读性：`id`、`class`、`name`、`data-xxx`、`src/for/type/href`、`title/alt`
        ```
        <a id="..." class="..." data-toggle="modal" href="#">Example link</a>
        ```

        布尔值属性建议不添加属性值，如`disabled`、`checked`等

    *   __Class 和 ID__

        class应以功能或内容命名，不以表现形式命名；

        class和id使用小写字母单词组成，多个单侧使用中划线`-`分隔；

        id必须保证页面唯一；

        使用唯一id作为js hook，避免创建无样式信息的class，js hook的id建议以`js-`开头，如：`id="js-add"`。

    *   __CSS 和 JavaScript 引入__

        引入 CSS 是必须指明`rel="stylesheet"`;
        ```
        <link rel="stylesheet" href="page.css">
        ```

        引入 CSS 和 JavaScript 时无须指明 type 属性。

        在head中引入页面需要的所有CSS资源

        JavaScript 应当放在页面末尾，或采用异步加载

4.  __注释__

    *   __按模块添加注释__

        在每个模块开始和结束的地方添加注释，注释如下：
        ```
        <!-- 新闻列表模块 -->
        <!-- /新闻列表模块 -->
        ```
##  __CSS规范__

1.  __文件引用__

    *   __一律使用`link`的方式调用外部样式__

    *   __严禁在页面中使用`<style>`块__

    *   __严禁使用@import__

    *   __非特殊情况需要不允许使用行内样式__

2.  __命名__

    *   __Class和Id__

        使用单词和数字命名，使用中划线分隔单词和数字；

        不允许使用拼音，尤其是缩写的拼音、拼音与英文混合；

        全局公共样式使用`g-`开头；

        模块样式使用`m-`开头；

        纯交互行为使用`js-`开头；

3.  __格式__

    *   __书写格式__

        使用4个空格单位的缩进；

        选择器分组时，保持独立的选择器占用一行，以逗号`,`隔开；

        `>`、`+`、`~` 选择器的两边各保留一个空格;

        声明块的左括号`{`前添加一个空格；

        声明块的右括号`}`应单独成行；

        声明语句中的`:`后应添加一个空格；

        声明语句单独一行并以分号`;`结尾；

        一般以逗号分隔的属性值，每个逗号后应添加一个空格；

        属性选择器中的值必须用双引号包围。

        示例：
        ```
        .selector,
        .selector-secondary,
        .selector > nav {
            padding: 15px;
            margin-bottom: 15px;
            background-color: rgba(0,0,0,.5);
            box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
        }
        ```
    

4.  __语法规则__

    *   __属性顺序__

        遵循先布局后内容的顺序，推荐顺序：定位>盒模型>内容相关

        私有属性在前标准属性在后

        示例：
        ```
        .index {
            /* 定位 */
            position: absolute;
            top: 0;
            right: 0;
            bottom: 0;
            left: 0;
            z-index: 100;

            /* 盒模型 */
            display: block;
            box-sizing: border-box;
            width: 100px;
            height: 100px;
            padding: 10px;
            border: 1px solid #e5e5e5;
            border-radius: 3px;
            margin: 10px;
            float: right;
            overflow: hidden;

            /* 其他 */
            font: normal 13px "Helvetica Neue", sans-serif;
            line-height: 1.5;
            text-align: center;
            background-color: #f5f5f5;
            color: #fff;
            opacity: .8;
            cursor: pointer;
            -webkit-box-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
               -moz-box-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
                 -o-box-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
                    box-shadow: 1px 1px 5px rgba(0, 0, 0, .5);
        }
        ```

    *   __选择器__

        尽量减少id选择器的使用；

        如无必要，不得为 id、class 选择器添加类型选择器进行限定；

        选择器的嵌套层数应不大于3级，位置靠后的限定条件应尽可能精确；

    *   __引号使用__

        url() 、属性选择符、属性值使用双引号

    *   __值与单位__

        当数值为 0-1 之间的小数时，省略前面的0；`opacity: .8;`；

        长度为 0 时须省略单位。 (也只有长度单位可省)：`padding: 0 5px;`；

        RGB颜色值必须使用十六进制记号形式 `#rrggbb`。不允许使用 `rgb()`。

        颜色值可以缩写时，必须使用缩写形式，如`#aca`；

        颜色值中的英文字符采用小写，且不允许使用命名色值。
    
    *   __媒体查询（Media query）__

        Media Query 不得单独编排，应放在尽可能相关规则的附近

    *   __属性缩写与分拆__

        无继承关系时，使用缩写；`margin: 10px;`

        存在继承关系时，使用分拆方式:
        ```
        .m-detail {
        　　　font: bold 12px/1.5 arial, sans-serif;
        }
        .m-detail .info {
        　　　font-weight: normal;
        　　　font-size: 14px;
        }
        ```

    *   __尽量不使用`!important`申明__

    *   __属性前缀__

        带私有前缀的属性由长到短排列，按冒号位置对齐。
        ```
        .box {
            -webkit-box-sizing: border-box;
               -moz-box-sizing: border-box;
                    box-sizing: border-box;
        }
        ```
5.  __注释__

    *   __组件和模块需要有清晰的注释说明；__

    *   __普通注释（单行）使用 `/* 普通注释 */`；__

    *   __区块注释__
        ```
        /**
         * 模块: m-detail
         * 描述：实况详情模块
         * 应用：page detail, info and etc...etc
         */
        ```

6.  __模块化__

    *   __每个模块必须是一个独立的样式文件，文件名与模块名一致；__
    
    *   __模块样式的选择器必须以模块名开头以作范围约定；__

    *   __选择器必须是以模块前缀开头：`.m-current`__

        所有的选择器必须是以 g-, m-, ui- 等有前缀的选择符开头的，意思就是说所有的规则都必须在某个相对的作用域下才生效，尽可能减少全局污染。

    ```
    .m-current {
        background: #fff;
        color: #333;
    }
    .m-current-head {
        padding: 5px 10px;
        background: #eee;
    }
    .m-current-head .title {
        background: #eee;
    }
    .m-current-con {
        padding: 10px;
    }
    .m-current-con .info {
        font-size: 14px;
        text-indent: 2em;
    }
    .m-current-con {
        text-align: center;
    }
    .m-current-foot .more {
        color: blue;
    }
    ```
    >任何超过3级的选择器，需要思考是否必要，是否有无歧义的，能唯一命中的更简短的写法


##  __Javascript规范__

1.  __代码风格__

    *   __书写格式__

        +   使用 4 个空格作为一个缩进层级，不允许使用2个空格或`tab`字符；

        +   二元运算符两侧必须有一个空格，一元运算符和操作对象之间不允许有空格：
            ```
            var a = !arr.length;
            a++;
            a = b + c;
            ```

        +   用作代码块起始的左花括号`{`前必须有一个空格；

        +   `if / else / for / while / function / switch / do / try / catch / finally` 关键字后，必须有一个空格；

        +   在对象创建时，属性中的`:`之后必须有空格，`:`之前不允许有空格；

        +   函数声明、具名函数表达式、函数调用中，函数名和`(`之间不允许有空格；

        +   `,` 和 `;` 前不允许有空格。如果不位于行尾，`,` 和 `;` 后必须跟一个空格。

        +   在函数调用、函数声明、括号表达式、属性访问、`if / for / while / switch / catch` 等语句中，`()` 和 `[]` 内紧贴括号部分不允许有空格。

        +   单行声明的数组与对象，如果包含元素，`{}` 和 `[]` 内紧贴括号部分不允许包含空格。

        +   行尾不得有多余的空格。

        +   每个独立语句结束后必须换行。

        +   运算符处换行时，运算符必须在新行的行首。

        +   在函数声明、函数表达式、函数调用、对象创建、数组创建、`for` 语句等场景中，不允许在 `,` 或 `;` 前换行。

        +   不得省略语句结束的分号。

        +   在 if / else / for / do / while 语句中，即使只有一行，也不得省略块 {...}。

        +   函数定义结束不允许添加分号。

    *   __命名__

        +   `变量`、`函数`、`函数`的`参数` 使用`Camel(驼峰)命名法`；
        ```
        var loadingModules = {};
        function stringFormat(theString) {

        }
        ```
        +   `类`使用`Pascal命名法`，`类`的`方法`和`属性` 使用`Camel命名法`；
        ```
        function UserInfo(name, age) {
            this.name = name;
            this.age = age;
        }
        ```
        +   `常量` 使用 `全部字母大写，单词间下划线分隔` 的命名方式。
        ```
        var HTML_ENTITY = {};
        ```
        +   类名使用名词，函数名使用动宾短语，`boolean` 类型的变量使用 `is` 或 `has` 开头；
        ```
        function Engine(options) {
        }
        function getStyle(element) {
        }
        var isReady = false;
        var hasMoreCommands = false;
        ```

    *   __注释__

        +   单行注释必须独占一行，`//`后跟一个空格，缩进和下一行被注释说明的代码一致；

        +   避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。

        +   为了便于代码阅读和自文档化，以下内容必须包含以 `/**...*/` 形式的块注释中：文件、namespace、类、函数或方法、类属性、事件、全局变量、常量、AMD 模块；文档注释前必须空一行；类型定义都是以 `{` 开始, 以 `}` 结束。
        ```
        /**
         * 函数描述
         *
         * @param {string} 
         * @param {number=} 
         * @return {Object} 返回值描述
         */
        ```

        +   文件顶部必须包含文件注释，用 `@file` 标识文件说明。文件注释中可以用 `@author` 标识开发者信息。
        ```
        /**
         * @file Describe the file
         * @author XXX
         */
        ```

    *   __语法特性__

        +   变量、函数在使用前必须先定义。
        
        +   每个 var 只能声明一个变量。

        +   变量必须 即用即声明，不得在函数或其它形式的代码块起始位置统一声明所有变量。

        +   在 `Equality Expression（相等表达式）`中使用类型严格的 `===`。仅当判断 `null` 或 `undefine`d 时，允许使用 `== null`。

        +   不要在循环体中包含函数表达式，事先将函数提取到循环体外。

        +   对循环内多次使用的不变值，在循环外用变量缓存。

        +   对有序集合进行遍历时，缓存 `length`。

        +   字符串开头和结束使用单引号 `'`。使用 `数组` 或 `+` 拼接字符串。使用数组字面量 `[]` 创建新`数组`

        +   使用对象字面量 `{}` 创建新 `Object`。

        +   避免不必要的DOM操作，缓存数组长度。

##  __图片规范__

*   __所有图片必须经过一定的压缩和优化才能发布使用；__

*   __保证视觉效果的前提下选择最小的图片格式和图片质量，以减少加载时间；__

*   __运用css雪碧图集中处理小的背景图和图标，注意，请务必在对应的精灵图psd源图中划参考线，并保存至img目录下；__

*   __内容图片建议使用jpg，可以拥有更好地显示效果，装饰性图片使用PNG。__

*   __半透明图片使用png24格式，严禁使用gif格式。__

##  __文件目录__

*   __`css`文件夹存放CSS文件；__

*   __`js`文件夹存放js文件；__

*   __`img`文件夹存放图片；__

*   __`fonts`文件夹存放字体文件；__

*   __`scss`文件夹存放SCSS文件；__

*   __`backup`文件夹存放.bak备份文件。__
