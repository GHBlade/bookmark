# 前端编码规范

###一般规范
* 文件/资源命名
>同一命名约定：以可读性而言，减号（-）是用来分隔文件名的不二之选
>文件命名总是以字母开头而不是数字<br>
>资源的字母名称必须全为小写<br>
>特殊情况：对文件增加前后缀或特定的扩展名（如 `.min.js`, `.min.css`,`3fa89b.main.min.css`）<br>
>示例：`my-file.min.css`,`my-script.js`

* 协议
>不要指定引入资源所带的具体协议 （http:, https:）<br>
>不指定协议使得 URL 从绝对的获取路径转变为相对的，在请求资源协议无法确定时非常好用，而且还能为文件大小节省几个字节<br>
>示例：`<script src="//cdn.com/foundation.min.js"></script>`

* 文本缩进
>一次缩进两个空格

* 注释
>不要写你的代码都干了些什么，而要写你的代码为什么要这么写，背后的考量是什么。也可以加入所思考问题或是解决方案的链接地址

* 代码检查
> [JSLint](http://www.jslint.com/),[JSHint](http://jshint.com/)

###HTML规范


###JavaScript规范


###CSS和Sass(SCSS)规范