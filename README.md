
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






