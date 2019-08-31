## CSS简单笔记

1. 例子

   ```css
   h2 {
       font-style: italic;
       font-weight: bold;
       font-size: 14px;
       font-family: "Microsoft YaHei",tahoma,"\5B8B\4F53";
       color: pink;
   }
   ```

   

2. **font-style**，字体样式，`normal或italic`

3. **font-weight**，字体粗细

   > 值有lighter、normal、bold、bolder、100~900（100的整数倍）
   >
   > normal相当于400，bold相当于700

4. **font-size**，字体大小，如`font-size: 30px`

5. **font-family**，字体中英文和Unicode码对照表

   ![字体中英文和Unicode码对照表](img/字体中英文对照表.jpg)

6. **font**，综合设置字体样式

   > font: font-style  font-weight  font-size/line-height  font-family;
   >
   > 须按以上顺序书写，以空格隔开
   >
   > font-size和font-family不能省略

7. 类的命名规范

   * 用横杠`-`，不要用下划线`_`
   * 不能以数字开头
   * 多个类名用空格隔开，`class="c1 c2"`
   * 样式显示效果与HTML元素中类名先后顺序无关，与CSS样式书写的上下顺序有关

8. 类选择器与Id选择器的区别

   * 类选择器可以重复使用
   * ID选择器只能一个元素使用

9. `*`星号，通配符选择器，代表所有选择器；但用的少。

   ```css
   * {
       color: red;
   }
   ```

   

10. `:`伪类选择器 - 链接伪类选择器

    - **:link**，未访问的链接

    - **:visited**，已访问的链接

    - **:hover**，鼠标移动到链接上

    - **:active**，选定的链接，点击鼠标不松开时

    - 注意书写顺序，须按lvha顺序书写

      ```html
      <style>
          a:link {
              color:blue;
          }
          a:visited {}
          a:hover {}
          a:active {}
      </style>
      <div>
          <a href="#" >秒杀</a>
      </div>
      ```

      

11. 伪类选择器 - 结构（位置）伪类选择器（指定选择器）

    * **first-child**，选取属于其父元素的首个子元素

    * **last-child**，选取属于其父元素的最后一个子元素

    * **nth-child(X)**，匹配属于其父元素的第X个子元素，`nth-child(even)`：匹配所有偶数，odd-奇数

    * **nth-last-child(X)**，倒数

      ```html
      <style>
          li:first-child {
              color:red;
          }
          li:nth-child(2n) { /*第2、4、6个孩子变蓝色*/
              color:blue;
          }
      </style>
      <ul>
          <li>第1个孩子</li>
          <li>第2个孩子</li>
          <li>第3个孩子</li>
          <li>第4个孩子</li>
          <li>第5个孩子</li>
          <li>第6个孩子</li>
          <li>第7个孩子</li>
      </ul>
      ```

      

12. 伪类选择器 - 目标伪类选择器

    * **:target**，用于选取当前活动的目标元素

      ```html
      <style>
          :target {
              color:red;
              font-size:30px;
          }
      </style>
      <div>
          <a href="#two" >跳到第二段</a>
          <h4 id="one">第一段</h4>
          <h4 id="two">第二段</h4>
          <!--通过a链接跳到第二段，第二段会变成“:target”指定的样式-->
      </div>
      ```

      

13. CSS外观属性

    * **color**
      1. `color: red;`
      2. `color: #FF00FF00;`
      3. `color: rgb(203,23,223);`
      4. `color: rgba(0,0,0,0.5);`，a的取值范围0~1
    * **text-align**，水平对齐方式
      * `text-align: center`;
      * 值有left、center、right等
    * **line-height**，行距
      * `line-height: 22px;`
      * 一般行距比字号大7~8像素即可
    * **text-indent**，首行缩进
      * `text-indent: 2em`
      * 1em就是一个字的宽度
    * **letter-spacing**，字（字母）间距
      * `letter-spacing: 2px`
      * 允许负值，默认normal
    * **word-spacing**，单词间距
      * `word-spacing: 10px;`
      * 对中文无效
    * **text-shadow**，文字阴影
      * `text-shadow: 5px 11px 3px rgba(0,0,0,0.5) `
      * `text-shadow: 水平位置(必填) 垂直位置(必填) 模糊距离(选填) 阴影颜色(选填)`
      * 英文：`text-shadow: h-shadow v-shadow blur color`

14. sublime快捷键，xxx+tab

    * `div*10`，10个div
    * `ul>li*5`，ul下面5个li
    * `div+p+div`，兄弟关系，依次创建div，p，div
    * `.first-class`，即`<div class="firsti-class"></div>`
    * `#firstid`，即`<div id="firstid"></div>`
    * `p.first-class`，即`<p class="first-class"></p>`

15. 三种样式表

    1. 行内样式表

    2. 内部（内嵌）样式表

    3. 外部样式表 

       `<link ref="stylesheet" href="style.css" type="text/css" />`

16. 行内（内联）元素特点

    1. 和相邻行内元素在一行上
    2. 高、宽无效，但水平方向的padding和margin可以设置，垂直方向的无效
    3. 默认宽度就是本身内容的宽度
    4. 行内元素只能容纳文本或其他行内元素。（a特殊）
    5. 另外：
       * p、h1~h6、dt都是文本块级元素，里面不能放块级元素
       * a元素里面不能再放a

17. 块级元素特点

    1. 总是从新行开始
    2. 高度、宽度、内边距、外边距都可以控制
    3. 宽度默认是100%
    4. 可以容纳内联和块级元素

18. 行内块元素（inline-block）

    * 有：img，input，td；可以设置宽高和对齐属性

    * 特点：高度，宽度，外内边距都可以控制

19. 行内与块级别互相转换

    > display: block; 转为块级元素
    >
    > display: inline; 转为行内元素
    >
    > display: inline-block; 转为行内块元素
    >
    > display: flex; 伸缩布局，按比例分空间，子元素flex:1;
    >
    > display: none;  隐藏元素，不保留位置（类似Android的View.GONE）
    >
    > visibility: hidden/visible; 隐藏/显示元素，保留位置（类似Android的View.VISIBLE）

20. 复合选择器

    * 交集选择器`div.c1`，表示类名为`c1`的`div`

    * 并集选择器`div,p`，用逗号隔开，书写规范为每个逗号占一行

    * 后代选择器`div p`，用空格隔开

    * 子元素选择器`ul>li`，用大于号；也叫儿子选择器，不包括孙子

    * 属性选择器 `a[name]`，用中括号；

      * `a[name]`，表示选择设置了name属性的所有a标签

      * `input[type=text]`，表示所有`type="text"`的input标签

      * `div[class^=font]`，表示class名以font开始的div；

        ```html
        <style>
            div[class^=font] { /*类名为font1、font2、font3的颜色改为blue*/
                color:blue;
            }
        </style>
        <div class="font1">选择器1 </div>
        <div class="font3">选择器12 </div>
        <div class="font2">选择器13 </div>
        <div class="abd">选择器1 </div>
        ```

      * `div[class$=font]`，以font的结尾

      * div[class*=font]，任意位置有font即可

    * 伪元素选择器`E::first-letter`

      * **E::first-letter**，文本的第一个单词或字

      * **E::first-line**，文本第一行

      * **E::selection**，可改变选中文本的样式

        ```css
        p::selection {
        	color: pink;
        }
        ```

      * **E::before**，在元素内部的前面插入content，

        ```css
        div::before {
            content: "俺";
        }
        ```

      * **E::after**，在元素内部的后面插入

21. CSS书写规范

    1. 并集选择器换行显示，如：

       ```css
       p,
       div,
       .user {
           color：red;
       }
       ```

    2. 选择器的嵌套层级不要超过3级

    3. 属性以分号结尾

22. **背景**

    ```css
    div {
    	background-color: #f00;/*带透明度的写法：rgba(255,0,0,0.5),错误写法：#5f00*/
    	background-image: url(liu.jpg);
    	background-repeat: repeat;
        /*默认repeat，repeat, repeat-x, repeat-y, no-repeat */
    	background-position: 10px bottom; 
        /*(left/right/center/10px top/bottom/center/10px) */
        background-attachment: fixed;
        /*fixed、scroll; 背景附着，默认scroll，随滚动条一起滚动；*/
        background-size: 100px 50%; 
        /*图片宽高设置，(宽度 高度)，可以是px、百分比、
        cover（等比例缩放到铺满，图片可能部分不可见）、
        contain（等比例缩放到其中一边与容器边相等）*/
    }
    ```

23. 背景简写，颜色》图片》平铺》滚动》位置

    ```css
    background: #f00 url(liu.jpg) repeat fixed 10px bottom;
    ```

24. 设置一行**文字水平垂直居中**

    ```css
    a {
        text-align: center;/*水平居中*/
        line-height: 22px;/*间接做到垂直居中，让行高等于a容器的高度*/
        text-decoration: none;
        /*文本装饰，取消下划线；值：none、underline、overline、line-through*/
    }
    ```

    

25. 定位属性`position`

    ```css
    position: absolute; /*static，relative，absolute，fixed */
    ```

    - **static**：默认，

    - **relative**：相对定位，不脱标，占有位置

      ```css
      position: relative;
      left: 100px; /*相对于自己往右偏移100px，但原来的位置还是占着*/
      ```

    - **absolute**：绝对位置，完全脱标，不占有位置，飘在其他标签上方

      ```css
      position: absolute; 
      left: 100px; /*如果父元素没有定位，则孩子以浏览器准对齐*/
      ```

      > 如果父元素没有定位，则孩子以浏览器准对齐；

      > 如果父元素有定位（如relative，absolute），则孩子以最近的父元素为基准对齐，且不受父元素padding影响。

      > 一般用法：子绝父相，孩子绝对定位，父亲相对定位。

      孩子居中的方法：

      ```css
      left: 50%;
      margin-left: -(自己宽度/2)px; /*或者 transform: translate(-50%); */
      /*设置了绝对定位后原来通过magin设置居中的方法无效了，margin: 0px auto;*/
      ```

      

    - **fixed**：固定定位，不受父元素影响，只认浏览器；完全脱标，不占位置，不随滚动条滚动。

      > 固定定位的盒子一定要写宽高，除非有内容撑开不用写。

    - 另外，position的绝对和固定定位与float都会使元素变为行内块元素

26. **z-index**：设置堆叠顺序

    ```css
    position: absolute;
    z-index: 1; /*默认0，没有单位*/
    ```

    

27. **overflow**：溢出，设置内容超过指定宽高时的显示

    - visible：默认，没有滚动条，会溢出；
    - auto：超出显示滚动条，不超出不显示滚动条，不会溢出；
    - hidden：超出部分不显示，没有滚动条，不会溢出；
    - scroll：总是显示滚动条，不会溢出；

28. **box-shadow**：盒子阴影

    `box-shadow:  水平阴影 垂直阴影 模糊距离 阴影尺寸 阴影颜色 内/外阴影;`

    ```css
    box-shadow: 0 2px 5px rgba(0,0,0,0.2);
    ```

    - h-shadow: 必填，水平阴影位置，允许负值；
    - v-shadow: 必填，垂直阴影位置
    - blur: 可选，模糊距离
    - spread: 阴影尺寸
    - color: 阴影颜色
    - inset:  将外部阴影（outset）改为内部阴影

29. 

## CSS高级功能

##### cursor鼠标样式

```css
cursor: default; 箭头
cursor: pointer; 小手
cursor: move; 移动
cursor: text; 文本
```

##### outline轮廓线

```css
outline: 0; 取消轮廓线，如取消input的轮廓线，0或none效果一样；
outline: 1px solid red; 在border的外面是outline，与border不冲突。
border: 1px solid blue;
```

##### 取消文本域textarea可拖拽

```css
resize: none;
```

##### vertical-align控制行内块元素和文本对齐方式

通常用来控制图片和表单与文字的对齐。

```css
vertical-align: baseline(默认) | top | middle | bottom;
```

```css
textarea {
    vertical-align: middle;
}
<div>
	姓名：<textarea></textarea>
</div>
```

##### 去除图片底侧空白缝隙

记住：图片、表单等行内块元素的底线会和父级盒子的基线对齐，造成图片底侧有空白缝隙；

解决方法：

 - 把行内块元素转为块元素

   ```css
   img {
       display: block;
   }
   ```

 - 不和基线对齐，改为top对齐

   ```css
   img {
       vertical-align: middle|top; 一般用top
   }
   ```

##### 文本换行规则设置

- **word-break**：英文单词自动换行规则

  ```css
  word-break: normal | break-all | keep-all; 
  /*
  normal和keep-all换行需保持单词完整，只能在半角空格或连字符处换行；
  break-all可在任意字母位置换行
  */
  ```

  

- **white-space**：

  ```css
  white-space: normal; 默认，显示不玩自动换行
  white-space: nowrap; 强制同一行内显示所有文本，直到遇到br等换行元素
  ```

- **text-overflow**，一行文字溢出处理，需与white-space和overflow一起用才有效

  ```css
  white-space: nowrap; 	强制行内显示
  overflow: hidden;		超出部分不显示	
  text-overflow: clip;	不带省略号
  text-overflow: ellipsis; 带省略号
  ```

##### 精灵图(Sprite)

```css
span {
    width: 20px;
    height: 20px;
    background: url(image/abcd.jpg) no-repeat;
    background-position: 0 -388px;
}
```

##### 图标字体

使用步骤：

 1. 声明字体

 2. 引用字体

    ```css
    span {
        font-family: "字体库名"; 
    }
    ```

 3. 在布局中写入图标字体

    ```css
    <span>  </span> /*图标字体是不可见*/
    或者
    span::before{
        content: "\e900";
    }
    ```

http://icomoon.io

http://www.iconfont.cn



##### 滑动门

```html
<!--a负责左侧背景，span负责右侧背景，不能给宽度，用padding-->
<style>
    a {
        display: inline-block;
        height: 33px;
        background: url(images/ao.png) no-repeat;
        padding-left: 15px;
    }
    a span {
        display: inline-block;
        height: 33px;
        background: url(images/ao.png) no-repeat right; 背景图右对齐
        padding-right: 15px;
    }
</style>
<li>
	<a href="#">
    	<span>导航栏</span>
    </a>
</li>
```



##### 将padding和border都计入width/height里面

```css
box-sizing: border-box; 
```



##### 过渡动画

```css
/*实现鼠标移到div上变宽动画*/
div {
    width: 200px;
    height: 100px;
    background: pink;
    /*transition不能写在div:hover里面*/
    /*transition: 要过渡的属性  耗时  运动曲线  延迟多久开始 */
    transition: width 0.3s ease-in 0s;
    /*运动曲线：linear|ease(默认)|ease-in|ease-out|ease-in-out
    		    匀速 |逐渐慢下来 | 加速  |  减速   |先加速后减速 */
    /*先宽度动画后高度动画*/
    transition: width 0.3s ease-in 0s, height 0.6 ease 0s;
    /*所有变化都实现0.6s的动画，如宽度和高度同时动画*/
    transition: all 0.6s;
}
div:hover {
    width: 600px;
    height: 300px;
}
```



## 变形 transform

- **平移translate**

  ```css
  transform: translate(50px, 50px); 移动X,Y
  transform: translate(50px);	 移动X
  transform: translate(50%);	移动X，移动自己宽度的一半，与父级无关
  transform: translate(0, 50px); 移动Y
  transform: translateX(50px);  移动X
  transform: translateY(50px);   移动Y
  transform: translateZ(100px);只能是px不能是百分比，正值放大效果，要与perspective配合使用
  transform: translate3d(0, 30px, 0);  合写，分别代表x,y,z轴
  ```

  

- **缩放scale**

  ```css
  transform: scale(2); 宽高放大到原来的2倍
  transform: scale(0.5, 2); 宽缩小，高放大
  ```

  

- **旋转rotate(deg)**

  ```css
  transform: rotate(90deg);  顺时针旋转90度
  transform: rotateZ(90deg); 顺时针旋转90度
  transform: rotateX(180deg);  沿X轴旋转
  transform: rotateY(360deg);  沿Y轴旋转
  ```

  

- **指定基准点旋转transform-origin**

  ```css
  transform: rotate(90deg);
  transform-origin: left top;  以左上角为基准点旋转，还有right bottom
  transform-origin: 10px 10px;  以指定的点旋转
  ```

  

- **倾斜skew(deg,deg)**

  ```css
  transform: skew(-10deg, 0);  往右倾斜
  ```

  

- **视距效果perspective**

  写在父元素里

  ```css
  body {
      perspective: 1000px;    值越小效果越明显，默认0；
  }
  ```

  

- **背面可见性backface-visibility**

  ```css
  backface-visibility: hidden;  当元素旋转到背面时变为不可见。
  ```

  

- **动画animation**

  ```css
  animation: 动画名称 动画时间 运动曲线 何时开始 播放次数 是否反方向
  /*例子*/
  div {
      animation: go 2s ease 0s infinite alternate;
  }
  /*定义动画*/
  @keyframes go {
      from {
          transform: translateX(0);
      }
      to {
          transform: translateX(200px) rotateY(30deg); 多组动画用空格隔开
      }
  }
  ```

  

- 

## 三等份布局

```css
section {
    display: flex; 1.父盒子设置伸缩布局
    flex-direction: row; 2. 指定水平(row)等分/垂直(column)等分,默认row
    min-width: 100px;  可限制最大最小宽高
    max-width: 600px; 
}
/*设置第一个div与第二个div的宽度比例为1：2*/
section div: nth-child(1) {
    flex: 1;
}
section div: nth-child(2) {
    flex: 2;
}
```

1. 水平排列方式**justify-content**:

   ```css
   display: flex;
   justify-content: flex-start; 默认，让子元素靠左对齐
   justify-content: flex-end;   让子元素靠右对齐
   justify-centent: center;	让子元素居中对齐
   justify-content: space-between; 左右的子元素贴近父容器，中间的平均分布空白间距
   justify-content: space-around;  每个子元素均分空白间隙
   ```

2.  垂直排列方式**align-content**:

   用法同justify-content；

   起作用的条件：

    ```css
   display: flex;
   flex-direction: row;  横向排列
   flex-wrap: wrap;   换行
    ```

   

3.  单行在容器中的垂直位置**align-items**:

   ```css
   align-items: stretch;
   align-items: center;
   align-items: flex-start;
   align-items: flex-end;
   ```

   

4. 显示不下是否拆行**flex-wrap**：

   ```css
   flex-wrap: nowrap; 默认，不换行，显示不下则压缩显示
   flex-wrap: wrap;  显示不下时换行
   flex-wrap: wrap-reverse; 将wrap按x轴翻转
   ```

   

5. 简写**flex-flow: flex-drection flex-wrap;**

   ```css
   flex-flow: row wrap;
   ```

6. 控制子元素的排列顺序**order**

   ```css
   /*让第二个盒子排在第一个前面*/
   div:nth-child(1) {
       order: 1;
   }
   div:nth-child(2) {
       order: -1;
   }
   ```

   

7. 



​	

