## rem基础

> rem,（root em）相对单位，相对于html元素的字体大小（font-size）的倍数
>
> em，是相对父元素字体大小的倍数



## 媒体查询（Media Query）

监听宽度变化，可以根据不同的屏幕尺寸使用不同的样式；

格式：

> @media mediatype  and|not|only  (media feature) {
>
> ​	CSS-Code;
>
> }

- 媒体类型（mediatype）值有：
  1. all: 所有设备
  2. print： 打印机
  3. screen：电脑，平板，手机等
- 关键字
  1. and：加某个媒体类型，且
  2. not：排除某个媒体类型，非
  3. only：指定某个特定的媒体类型，可省略
- 媒体特性（media feature）
  1. width
  2. min-width，大于等于
  3. max-width，小于等于
- 例子

```css
//如果在我的屏幕上宽度小于等于800px，则背景颜色为pink
@media screen and (max-width: 800px) {
    body {
        background-color: pink;
    }
}
// 400px到800px
@media screen and (min-width: 400px) and (max-width: 800px) {
    html {
        font-size: 50px;
    }
}
```

- 引入资源

  根据不同的屏幕尺寸使用不同的css样式表

  ```html
  <head>
      <link rel="stylesheet" href="style320.css" media="screen and (min-width: 320px)">
      <link rel="stylesheet" href="style640.css" media="screen and (min-width: 640px)">
  </head>
  ```

  



## Less基础

#### 介绍

Leaner Style Sheets 精简样式表，CSS扩展语言，也称为CSS预处理器；

[官网](http://lesscss.cn)

常见的CSS预处理器：Sass、Less、Stylus



#### 使用

- 新建`.less`文件

- 变量

  > @变量名:值;  //变量名大小写敏感

  ```less
  @color: pink;
  body {
      background-color: @color;
  }
  div {
      color: @color;
  }
  ```

- Less嵌套

  ```less
  .header {
      width:200px;
      height:200px;
      background-color: pink;
      //子元素的样式可以直接写在父元素样式里面
      a {
          color: red;
          //有&用于交集、伪类、伪元素选择器
          &:hover {
          	color: blue;
      	}
      }
      &::before {
          content: "";
      }
  }
  ```

  

- Less运算

  数字、颜色、变量都可以运算

  ```less
  //运算符左右两侧必须有空格
  @border: 5px * 2;
  div {
      width: 200px - 50;
      height: 400px / 2;
      border: @border solid red;
  }
  @baseFont: 16px;
  img {
      //如果两个数都有单位，以第一个单位为准
      width: 82rem / @baseFont;
      background-color: #666 - #222;
  }
  
  
  ```

  

## rem适配方案

#### 方案一、less+媒体查询+rem



#### 方案二、flexible+rem



