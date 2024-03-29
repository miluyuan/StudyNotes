[TOC]

## 语法

#### 数据类型

> 数值Number、字符串String 、布尔Boolean、undefined、null、Object；

> 谷歌浏览器上日志颜色：字符串-黑色、数值和布尔蓝色、undefined和null灰色。

```javascript
 console.log('ss', 2, null, undefined, true);
```



#### 类型转换

- 数值转字符串

  ```js
  //转为字符串
  var n = 6;
  var s = n.toString();
  console.log(typeof s); //string
  var s = String(n);
  var s = ''+n;
  ```

  

- 字符串转数值

  ```js
  var a = '1';
  // Number
  var b = Number(a);
  var c = Number('c'); //NaN
  var d = Number(null); //0
  var e = Number(undefined); //NaN
  // parseInt
  var a = parseInt('2'); //2
  var b = parseInt('k23'); //NaN
  var c = parseInt(null); //NaN
  var d = parseInt(undefined); //Nan
  //parseFloat
  var a = parseFloat('1.23df'); //1.23
  var b = parseFloat('1.3.4.5'); //1.3
  var c = parseFloat('h34'); //Nan
  var d = parseFloat(null); //Nan
  var e = parseFloat(undefined); //Nan
  ```

  

- 布尔与字符串和数值的转换

  ```js
  var a = Boolean('0'); //true,字符串只要有内容就为true
  var b = Boolean(0); //false，数值只要不是0都为true
  var c = Boolean('2'); //true
  var d = Boolean(null); //false
  var e = Boolean(undefined); //false
  var f = Boolean(''); //false
  ```

  

## 对象

#### 遍历对象的属性值

```js
var obj = {
    name:'小凤',
    age: 16,
    sex: '女'
}
for(var k in obj){
    console.log(obj[k]); //结果为：小凤 16 女
}
//数组也可以
var arr = [2,4,5,6,8];
for(var k in arr){
    console.log(arr[k]);
}
```

#### 删除对象的某个属性

```js
var obj = {
    name:'小凤',
    age: 16,
    sex: '女'
}
//删除年龄属性
delete obj.age;
```



#### 数组方法

```js
var arr = [2,3,4,5,6,2];
arr.length;
arr.push(9); //末端添加元素
arr.pop();  //删除末端元素
var arrSlice = arr.slice(2,4); //截取arr中的元素，不包括4，arr不变
var arr2 = ['7','8','9'];
var arrConcat = arr.concat(arr2); //合并数组返回新数组，原数组不变
var s = arr.join(); //返回以逗号隔开的字符串，如“2,3,4”
var s1 = arr.join("-"); //返回以“-”隔开的字符串
```







# 常用Web Api

## DOM（Document Object Model 文档对象模型）

## 获取元素

```html
<div class='box'>
    <ul id='ulid' class='cls'>
        <li>项目1</li>
        <li>项目2</li>
    </ul>
</div>
```

```js
document.getElementById('ulid'); //返回整个ul元素
document.getElementsByClassName('cls'); //返回集合
document.getElementsByTagName('li'); //返回集合
// document.querySelector('选择器')
document.querySelector('.cls'); //返回指定类名的元素集合的第一个元素
document.querySelector('#ulid'); //传入选择器格式的字符串
document.querySelectorAll('.box'); //返回对象集合
```

#### 获取特殊元素

```js
document.body //返回body元素
document.documentElement //返回html元素
```

#### 打印对象详细信息document.dir(element)



## 事件监听

```js
var btn = document.getElementById('btn');
btn.onclick = function() {
    alert("点秋香");
}
var input = document.querySelector('input');
input.onfocus //获得焦点
input.onblur //失去焦点
input.onmouseover //鼠标经过
input.onmouseout  //鼠标移开
div.onmouseenter  //鼠标经过，不会冒泡，即移到子元素不会触发父元素
div.onmouseleave  //鼠标移开，不会冒泡
```



## 操作元素

#### 改变元素内容

```js
var div = document.querySelector('div');
div.innerText = '时间'; //改变元素内容
div.innerHTML = '<strong>时间</strong>'; //改变元素内容，能识别html，常用
```

#### 修改元素属性

```js
var img = document.querySelector('img');
img.src = 'images/zxy.jpg';
img.title = '张学友';
```

#### 修改表单属性

> type、value、checked、selected、disabled

```js
var input = document.querySelector('input');
input.value = "被点击了";
input.disabled = true;
```

#### 修改样式属性

```js
var div = document.querySelector("div");
//element.style 这种方式修改的是行内样式，权重高;用于修改少量简单样式，多个样式用div.className
div.style.backgroundColor = 'pink'; //注意属性名称都变为驼峰命名了
div.style.width = '200px';
//element.className 修改类名，会覆盖之前类名
div.className = 'change';
```

#### 获取属性值的两种方式

```js
div.id //这种方式只能获取内置的属性值
div.getAttribute('id');//这种方式还是可以获取自定义的属性值
div.setAttribute('id', 'newId'); //设置属性的值，如果没有则直接创建并赋值
div.removeAttribute('id'); //移除属性
```

#### 自定义属性的规则

> 自定义属性以**‘data-xxx’**形式命名，用于区分内置属性
>
> 通过element.dataset.xxx得到属性值，dateset键值对集合
>
> dataset只能获取以”data-“开头的属性

```js
div.setAttribute('data-list-name', 'lisi');
//获取自定义属性的3种方式
div.dataset.listName //注意list-name会变为驼峰命名listName
div.dataset[listName]
div.getAttribute('data-list-name')
```

#### 节点操作

所有内容都是节点，包括文档、元素、属性、文本、注释等；

节点有三个属性：nodeType（节点类型）、nodeName（节点名称）、nodeValue（节点值）；

##### 1. 节点类型nodeType

	- 元素节点 nodeType=1，主要操作元素节点
	- 属性节点 nodeType=2
	- 文本节点 nodeType=3 （空格、换行等）

##### 2. 获取节点

- 获取父节点

  ```js
  var div = document.querySelector('div');
  div.parentNode //获取父节点，如没有则返回null
  ```

- 获取子节点

  ```js
  var div = document.querySelector('div');
  div.childNodes //返回集合，获取所有节点，里面包括文本节点，通过nodeType过滤文本节点
  div.children  //返回集合，获取子元素节点，常用
  div.firstChild //返回第一个子节点，可能是文本节点；div.lastChild 同
  div.firstElementChild //返回第一个子元素节点; div.lastElementChild 同
  div.children[0] //同firstElementChild
  ```

- 获取兄弟节点

  ```js
  var div = document.querySelector('div');
  div.nextSibling     //包括文本节点；div.previousSibling
  div.nextElementSibling //下一个元素节点，没有则返回null
  div.previousElementSibling
  ```

  


#####  3. 创建节点

```js
var ul = document.querySelector('ul');
var li = document.createElement('li');//创建节点
ul.appendChild(li); //添加节点
ul.insertBefore(li, ul.children[0]); //指定加入位置，在前面添加节点li
```

#####  4. 删除节点

```js
var ul = document.querySelector('ul');
ul.removeChild(ul.children[0]); //删除指定元素
```

取消链接跳转`href="javascript:;"`

```html
<a href="javascript:;"></a>
```

#####  5. 复制节点

```js
var ul = document.querySelector('ul');
//node.cloneNode(); 参数为空或false表示浅拷贝，不复制内容
var clone = ul.children[0].cloneNode();
//node.cloneNode(true); 深拷贝，复制内容
var clone = ul.children[0].cloneNode(true);
```

#####  6. 三种创建元素方式的区别

- document.write()

  ```js
  document.write('<div>123</div>');
  //缺点：会导致页面重绘，其他元素都没了
  ```

- innerHtml

  > 当创建很多个元素时：
  >
  > innerHtml如果用字符串拼接效率非常低（3000ms，比createElement低很多，createElement20ms）
  >
  > innerHtml如果采用字符串数组的形式拼接，效率很高（8ms，比createElement还高）

  ```js
  //字符串数组的形式拼接效率高
  var arr = [];
  for(var i =0, i<100, i++) {
      var li = "<li></li>";
      arr[i] = li;
  }
  div.innerHtml = arr.join("");
  ```

- document.createElement()





## 事件高级用法

#### 1. 添加事件(添加监听)

- eventTarget.addEventListener(type, listener[, useCapture])

  > 通过这种方式，同一个事件可以添加多个监听器
  >
  > type: 事件类型字符串，如click、mouseover，注意不带on
  >
  > listener：事件处理函数，事件发生时调用该函数
  >
  > useCapture：可选，boolean值，默认false，按冒泡顺序依次调用事件；true捕获顺序

  ```js
  //addEventListener(type, listener[, useCapture])
  //添加多个监听事件
  btn.addEventListener('click', function(){
      alert(22);
  })
  btn.addEventListener('click', function(){
      alert(33);
  })
  ```

#### 2. 删除事件

```js
btn.onclick = null;
btn.removeEventListener('click', 函数名);
```



#### 3. 事件对象event

```js
div.onclick = function(event) {//event即事件对象
    console.log(event);
}
```

- 事件对象说明

  > 事件对象只有有了事件才会存在，她是系统自动创建，不需要我们传递参数;
  >
  > 里面是一系列相关数据的集合，如鼠标坐标等

- 事件常用属性和方法

  ```js
  e.target //点击的那个元素
  e.type   //事件类型，如click、mouseover、mouseout，不带on
  e.preventDefault(); //方法，阻止默认事件,如链接跳转
  e.stopPropagation(); //阻止冒泡，事件不会传给父元素
  
  
  var a = document.querySelector('a');
  a.addEventListener('click', function(e) {
      //阻止链接跳转
      e.preventDefault();
  })
  //传统注册方式直接return false; 也可以阻止跳转
  a.onclick = function(e) {
      return false;// 或 e.preventDefault();
  }
  ```


 #### 4. 事件委托

  > 原理：给父节点添加监听器，利用事件冒泡影响每个子节点

  ```js
  var ul = document.querySelector('ul');
  ul.addEventListener('click', function(e){
      e.target.style.backgroundColor = 'pink';
  })
  ```

 #### 5. 常用鼠标事件

- 禁止鼠标右键菜单

  ```js
  document.addEventListener('contextmenu', function(e) {
      e.preventDefault();
  })
  ```

- 禁止选中文字

  ```js
  document.addEventListener('selectstart', function(e) {
      e.preventDefault();
  })
  ```

- 鼠标事件对象**MouseEvent**

  ```js
  document.addEventListener('click', function(e) {
      e.clientX  
      e.clientY  //鼠标相对于浏览器窗口可视区的x、y坐标，与滚动条滚动无关
      e.pageX   
      e.pageY   //相对于文档的x、y坐标，与滚动条有关，常用
      e.screenX
      e.screenY  //相对于屏幕的坐标
  })
  ```

- 鼠标移动事件**mousemove**

  ```js
  document.addEventListener('mousemove', function(e) {
      var x = e.pageX;
      var y = e.pageY;
      img.style.left = x +'px';
      img.style.top = y + 'px';
  })
  ```

  


#### 6. 常用键盘事件

-  onkeyup      -e.keyCode不区分大小写
- onkeydown   -keydown比keypress先执行，e.keyCode不区分大小写
- onkeypress   -不能识别功能键：ctrl shift 左右箭头；e.keyCode区分大小写

- 键盘事件对象**KeyboardEvent**

  ```js
  document.addEventListener('keydown', function(e) {
      //不区分大小写，不管A还是a得到的都是大写A的keyCode
      console.log(e.keyCode);
  })
  document.addEventListener('keypress', function(e) {
      //区分大小写字母
      console.log(e.keyCode);
  })
  ```

  






## BOM（Browser Object Model）

#### 1. 页面加载事件

> window.onload，在界面完全加载完成（图像、脚本、css等）后调用；包括刷新、前进、后退都会调用

```js
window.onload = function() {}
或
window.addEventListener('load', function() {})
//页面显示监听，基本和onload一样；区别是load是重新加载，如果是已缓存好的页面则不会调load
window.onpageshow = function(e) {
    if(e.persisted) {// true，从缓存中加载的
        
    }
}  
```

> DOMContentLoaded,仅当DOM加载完成时调用，不用等css，图片，flash加载完成。

```js
window.addEventListener('DOMContentLoaded', function() {})
```



#### 2. 窗口大小调整事件

> window.onresize,

```js
//window可以省略
window.addEventListener('resize', function(){
    //窗口宽度小于800隐藏元素
    if(window.innerWidth <= 800){
        div.style.display = 'none';
    } else {
        div.style.display = 'block';
    }
})
```



#### 3. 定时器

> window.setTimeout(调用函数， [延迟的毫秒值]);
>
> 只调用一次

```js
setTimeout(function(){}, 2000);
//或传方法名
var fn = function(){}
setTimeout(fn, 2000);
//或传字符串
setTimeout('fn()', 2000);
//给定时器取名
var timeout = setTimeout(fn, 2000);
```

> window.clearTimeout(定时器名字)

```js
var timeout = setTimeout(function(){}, 2000);
clearTimeout(timeout);
```

> window.setInterval(调用函数， [延迟的毫秒值]);
>
> 重复调用，每隔指定时间调用，用法同setTimeout

> window.clearInterval(定时器名字)；



#### 4. 事件循环（event loop）



#### 5. location对象

- location的属性

  > window.location
  >
  > location.href   http://www.itcast.cn/index.html?name=andy&age=18#link
  >
  > location.host   www.itcast.cn
  >
  > location.port
  >
  > location.pathname    "index.html"
  >
  > location.search     "?name=andy&age=18"
  >
  > location.hash        "#link"
  >
  > 给location.href赋值会自动跳转到赋值的网址

- location的方法

  > location.assign('www.itcast.cn');   会记录浏览历史，可以实现后退功能
  >
  > location.replace('www.itcast.cn');  不会记录浏览历史，不可以实现后退功能
  >
  > location.reload();   刷新
  >
  > location.reload(true);  强制刷新

  




#### 6. navigator对象

> 判断浏览器是手机还是pc



#### 7. history对象

> history.back();  后台，history.go(1);
>
> history.forward(); 前进, history.go(-1);
>
> history.go(n);  前进或后退页数

#### 8. 物理像素比

window.devicePixelRatio

> pc端一般是1，手机端如Iphone6s是2



## 元素偏移量offset

#### 常用属性

> 属性值不带单位，值受父级是否有定位影响，是只读属性，只能获取值不能设值
>
> element.offsetParent       返回带有定位的父级元素，如果没有则返回body
>
> element.offsetTop        与上侧的距离
>
> element.offsetLeft
>
> element.offsetWidth   包括padding、border
>
> element.offsetHeight

#### offset与style区别

1. offset只读，不能设置
2. offset获取的是数值，style得到的是带单位字符串“200px”
3. style只能得到的是行内样式里设置的值
4. style.width 不包括padding和border
5. 所以，获取值用offset，设置值用style



## 元素可视区client

##### 常用属性

> 属性值不带单位
>
> element.clientTop   返回border-top
>
> element.clientLeft   返回border-left
>
> element.clientWidth  包括padding，不包括border
>
> element.clientHeight   

##### 立即执行函数

> 两种写法：
>
> (function(){})();
>
> 或
>
> (function(){}())



## 元素滚动scroll

#### 元素内容滚动

> 与滚动条有关，不带单位
>
> element.scrollTop    返回被卷去的上侧距离，不带单位
>
> element.scrollLeft 
>
> element.scrollWidth   返回内容的实际宽度，不含边框，最小值是element.clientWidth
>
> element.scrollHeight

#### 页面滚动

针对的是页面的滚动条

> 不带单位，获取值，不能赋值
>
> window.pageYOffset   头部被卷去的距离 
>
> window.pageXOffset   

> 不带单位，赋值，窗口滚动
>
> window.scroll(x, y); 
>
> window.scroll(0, 100); //滚动到100px位置

#### 滚动事件

```js
div.addEventListener('scroll', function() {
    console.log(div.scrollTop);
})
```

## offset、client、scroll区别

1. offset用于获取元素位置，offsetTop，offsetLeft
2. client用于获取元素大小，clientWidth，clientHeight
3. scroll用于获取滚动距离，scrollTop，scrollLeft
4. 页面滚动距离用window.pageYOffset，pageXOffset



##　移动端

#### 触摸事件

```js
// touchstart、touchmove、touchend
div.addEventListener('touchstart', function(e){
    //e:TouchEvent对象
    e.touches //获取屏幕上手指列表
    e.targetTouches //获取当前元素上手指的列表，常用
    e.changedTouches //手指状态发生改变的列表，离开的手指列表或增加的手指列表
     //获取第一个手指的信息，Touch对象
    e.targetTouches[0]
})
```

#### Touch对象

```js
var touch = e.targetTouches[0];
touch.clienX
touch.clienY
touch.pageX
touch.pageY
touch.screenX
touch.screeY
touch.target //被触摸的元素
```

#### 利用CSS3的过渡动画

```js
var index = 0;
var timer = setInterval(function(){
    index++;
    var translatex = -index * w;
    //实现轮播图移动动画
    ul.style.transition = 'all .3s';
    ul.style.transform = 'translateX(' + translatex + 'px)';
}, 2000);
//监听过度动画完成事件transitionend
ul.addEventListener('transitionend', function() {
    
})

```

#### 获取类名数组classList

```js
div.classList //返回DOMTokenList
var cls = div.classList[0] //获取第一个类名,返回字符串
```

- 添加类名

  ```js
  div.classList.add('three');//在后面追加类名
  ```

- 删除类名

  ```js
  div.classList.remove('three');
  ```

- 切换类名

  ```js
  div.classList.toggle('bg'); //当没有‘bg'这个类名时添加，已经有则删除
  ```

#### 移动端click事件会延迟300ms问题

> 原因是移动端有个双击缩放功能，300ms延迟用于判断是否双击

- 解决方法1

  缺点是双击缩放没了

  ```html
  <meta name='viewport' content='user-scalable=no'>
  ```

  

- 解决方法2

  利用touch事件自己封装点击事件，缺点是繁琐

- 解决方法3

  使用[fastclick插件](https://github.com/ftlabs/fastclick)，插件就是js文件，直接引入即可

#### 移动端插件

- 触摸滑动插件[swiper](www.swiper.com.cn)、superslide、iscroll

- 视频插件[zy.media.js]

#### 移动开发框架

- Bootstrap、Vue、jQuery
- 



## 本地存储

> 存储在浏览器中
>
> 只能存字符串，通过JSON.stringify()转为字符串存储

#### sessionStorage

- 存约5M数据
- 关闭浏览器数据消失
- 同一窗口（页面）数据可以共享
- 以键值对形式存数据

```js
window.sessionStorage.setItem(key, value);//设值， key是字符串
sessionStorage.getItem(key);	//取值
sessionStorage.removeItem(key); //删除数据
sessionStorage.clear();  //删除所有
```



#### localStorage

- 存约20M数据
- 数据永久有效，关闭浏览器不会消失
- 可以多窗口（页面）共享
- 存储与sessionStorage相同

```js
localStorage.setItem(key, value);//设值， key是字符串
localStorage.getItem(key);	//取值
localStorage.removeItem(key); //删除数据
localStorage.clear();  //删除所有
```





 