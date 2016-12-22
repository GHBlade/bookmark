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

* 全局命名空间污染与 IIFE(Immediately-Invoked Function Expression)
> IIFE 用以创建独立隔绝的定义域,还可确保你的代码不会轻易被其它全局命名空间里的代码所修改
```javascript
(function(log, w, undefined){
  'use strict';

  var x = 10,
      y = 100;

  // Will output 'true true'
  log((w.x === undefined) + ' ' + (w.y === undefined));

}(window.console.log, window));
```

* IIFE（立即执行的函数表达式）
> 无论何时，想要创建一个新的封闭的定义域，那就用 IIFE。它不仅避免了干扰，也使得内存在执行完后立即释放
```javascript
(function($, w, d){
  'use strict';// 严格模式

  $(function() {
    w.alert(d.querySelectorAll('div').length);
  });
}(jQuery, window, document));
```

* 严格模式
> ECMAScript 5 严格模式可在整个脚本或独个方法内被激活。它对应不同的 javascript 语境会做更加严格的错误检查

* 变量声明
> 总是使用 var 来声明变量。如不指定 var，变量将被隐式地声明为全局变量，这将对变量难以控制

* 定义域和定义域提升
> 在 JavaScript 中变量和方法定义会自动提升到执行之前

* 提升声明
> 只用一个 var 关键字声明，多个变量用逗号隔开<br>
> 把赋值尽量写在变量申明中

* 使用带类型判断的比较判断
> 使用 === 精确的比较操作符，避免在判断的过程中，由 JavaScript 的强制类型转换所造成的困扰<br>
> 如果你使用 === 操作符，那比较的双方必须是同一类型为前提的条件下才会有效

* 明智地使用真假判断
> if(a == true) 是不同于 if(a) 的。后者的判断比较特殊，我们称其为真假判断<br>
> 这种判断会通过特殊的操作将其转换为 true 或 false，下列表达式统统返回 false：false, 0, undefined, null, NaN, ''（空字符串）

* 变量赋值时的逻辑操作
> 逻辑操作符 || 和 && 也可被用来返回布尔值。如果操作对象为非布尔对象，那每个表达式将会被自左向右地做真假判断
> 不推荐：
```javascript
if(!x) {
  if(!y) {
    x = 1;
  } else {
    x = y;
  }
}
```
> 推荐：这一小技巧经常用来给方法设定默认的参数
```javascript
x = x || y || 1;
```

* 澄清：分号与函数
> 分号需要用在表达式的结尾，而并非函数声明的结尾
```javascript
var foo = function() {
  return true;
};  // semicolon here.

function foo() {
  return true;
}  // no semicolon here.
```

* 语句块内的函数声明
> 切勿在语句块内声明函数，在 ECMAScript 5 的严格模式下，这是不合法的,但在语句块内可将函数申明转化为函数表达式赋值给变量

* 异常
```javascript
if(name === undefined) {
  throw {
    name: 'System Error',
    message: 'A name should always be specified!'
  }
}
```

* 标准特性
> 为了最大限度地保证扩展性与兼容性，总是首选标准的特性，而不是非标准的特性<br>
> （例如：首选 string.charAt(3) 而不是 string[3]；首选 DOM 的操作方法来获得元素引用，而不是某一应用特定的快捷方法）

* 简易的原型继承
```javascript
(function(log){
  'use strict';

  // Constructor function
  function Apple(name) {
    this.name = name;
  }
  // Defining a method of apple
  Apple.prototype.eat = function() {
    log('Eating ' + this.name);
  };

  // Constructor function
  function GrannySmithApple() {
    // Invoking parent constructor
    Apple.prototype.constructor.call(this, 'Granny Smith');
  }
  // Set parent prototype while creating a copy with Object.create
  GrannySmithApple.prototype = Object.create(Apple.prototype);
  // Set constructor to the sub type, otherwise points to Apple
  GrannySmithApple.prototype.constructor = GrannySmithApple;

  // Calling a super method
  GrannySmithApple.prototype.eat = function() {
    // Be sure to apply it onto our current object with call(this)
    Apple.prototype.eat.call(this);

    log('Poor Grany Smith');
  };

  // Instantiation
  var apple = new Apple('Test Apple');
  var grannyApple = new GrannySmithApple();

  log(apple.name); // Test Apple
  log(grannyApple.name); // Granny Smith

  // Instance checks
  log(apple instanceof Apple); // true
  log(apple instanceof GrannySmithApple); // false

  log(grannyApple instanceof Apple); // true
  log(grannyApple instanceof GrannySmithApple); // true

  // Calling method that calls super method
  grannyApple.eat(); // Eating Granny Smith\nPoor Grany Smith

}(window.console.log));
```

* 使用闭包
> 闭包的创建也许是 JS 最有用也是最易被忽略的能力了.[关于闭包](http://jibbering.com/faq/faq_notes/closures.html)
```javascript
(function(log, w){
  'use strict';

  // numbers and i is defined in the current function closure
  var numbers = [1, 2, 3],
      i;

  numbers.forEach(function(number, index) {
    w.setTimeout(function() {
      w.alert('Index ' + index + ' with number ' + number);
    }, 0);
  });

}(window.console.log, window));
```

* eval 函数（魔鬼）
> eval() 不但混淆语境还很危险，总会有比这更好、更清晰、更安全的另一种方案来写你的代码，因此尽量不要使用 evil 函数

* this关键字
> 只在对象构造器、方法和在设定的闭包中使用 this 关键字

* 数组和对象的属性迭代
> 





###CSS和Sass(SCSS)规范
