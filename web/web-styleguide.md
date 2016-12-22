# 前端编码规范

###一般规范
* 文件/资源命名
>同一命名约定：以可读性而言，减号（-）是用来分隔文件名的不二之选
>文件命名总是以字母开头而不是数字<br>
>资源的字母名称必须全为小写<br>
>特殊情况：对文件增加前后缀或特定的扩展名（如 `.min.js`, `.min.css`,`3fa89b.main.min.css`）<br>
>示例：`my-file.min.css`,`my-script.js`

* 协议
>不要指定引入资源所带的具体协议 （`http:`, `https:`）<br>
>不指定协议使得 URL 从绝对的获取路径转变为相对的，在请求资源协议无法确定时非常好用，而且还能为文件大小节省几个字节<br>
>示例：`<script src="//cdn.com/foundation.min.js"></script>`

* 文本缩进
>一次缩进两个空格

* 注释
>不要写你的代码都干了些什么，而要写你的代码为什么要这么写，背后的考量是什么。也可以加入所思考问题或是解决方案的链接地址

###HTML规范
* 推荐使用 HTML5 的文档类型申明： `<!DOCTYPE html>`
* 最好不要将无内容元素的标签闭合：使用 `<br>` 而非 `<br />`(area, base, br, col, command, embed, hr, img, input, keygen,  link, meta, param, source, track, wbr)
* 脚本加载 ： 鉴于将脚本放在`<head>`中同步加载会导致页面显示延迟，影响用户体验，所以推荐如下：
> 脚本引用写在body结束标签之前，并带上async属性。（虽然老版浏览器中不会异步加载脚本，但只阻塞了body结束标签之前的DOM解析，新版会执行异步加载）
```html
<html>
  <head>
    <link rel="stylesheet" href="main.css">
  </head>
  <body>  
    <!-- 内容部分 -->
    <script src="main.js" async></script>
  </body>
</html>
```

* 语义化：有根据有目的地使用 HTML 元素，对于可访问性、代码重用、代码效率来说意义重大
* 多媒体回溯：对页面上的媒体而言，像图片、视频、canvas 动画等，要确保其有可替代的接入接口。图片文件我们可采用有意义的备选文本（alt），视频和音频文件我们可以为其加上说明文字或字幕
* 关注点分离：
> 关注点主要指的是：信息（HTML 结构）、外观（CSS）和行为（JavaScript）<br>
> 严格地保证结构、表现、行为三者分离，并尽量使三者之间没有太多的交互和联系<br>
> 在此之外，为使得它们之间的联系尽可能的小，在文档和模板中也尽量少地引入样式和脚本文件<br>
> 清晰的分层意味着:<br>
>  不使用超过一到两张样式表<br>
>  不使用超过一到两个脚本<br>
>  不使用行内样式<br>
>  不在元素上使用 style 属性<br>
>  不使用行内脚本<br>
>  不使用表象元素<br>
>  不使用表象 class 名

* HTML 内容至上
> 不要引入一些特定的 HTML 结构来解决一些视觉设计问题<br>
> 不要将 img 元素当做专门用来做视觉设计的元素<br>
> 不推荐：<br>
```html
<span class="text-box">
  <img src="square.svg" alt="Square" />
  See the square next to me?
</span>
```
> 推荐：<br>
```html
<span class="text-box">
  See the square next to me?
</span>
```
```css
/* We use a :before pseudo element with a background image to solve the problem */
.text-box:before {
  content: "";
  display: inline-block;
  width: 1rem;
  height: 1rem;
  background: url(square.svg) no-repeat;
  background-size: 100%;
}
```

* Type属性
> 省略样式表与脚本上的 type 属性(鉴于 HTML5 中以上两者默认的 type 值就是 text/css 和 text/javascript，所以 type 属性一般是可以忽略掉的)

* 可用性
> [ARIA 规则](http://rawgit.com/w3c/aria-in-html/master/index.html#recommendations-table)在一些语义化的元素上可为其添上默认的可用性角色属性，使用得当的话已使网站的可用性大部分成立。假如你使用 nav, aside,  main, footer 等元素，ARIA 规则会在其上应用一些关联的默认值

* ID 和锚点
> 通常一个比较好的做法是将页面内所有的头部标题元素都加上 ID. 这样做，页面 URL 的 hash 中带上对应的 ID 名称，即形成描点，方便跳转至对应元素所处位置

* 格式化规则
> 在每一个块状元素，列表元素和表格元素后，加上一新空白行，并对其子孙元素进行缩进。内联元素写在一行内，块状元素还有列表和表格要另起一行。

* HTML 引号
> 使用双引号("") 而不是单引号('')



###JavaScript规范


###CSS和Sass(SCSS)规范
