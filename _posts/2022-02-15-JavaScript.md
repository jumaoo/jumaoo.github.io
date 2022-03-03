---
title: JavaScript基础
categories:
- Notes
feature_text: |
  JavaScript基础


---





<!-- more -->

### JavaScript

##### 1 什么是JavaScript

一种编程语言，可以在网页上实现复杂的功能，交互等

##### 2 3种方式添加JavaScript

![image-20220209095851868](assets/pic/image-20220209095851868.png" | absolute_url }})

##### 3 标记

```html
<script>
</script>
```

##### 4 一些函数对象

```javascript
alert();
console.log("hello".length);  //在console中打印
console.log("hello".charAt(0));
console.log("hello,world".replace("hello","goodbye"));
console.log("hello,world".toUpperCase());
```

##### 5 新建变量、常量

- 变量

  ```
  var name = "aaa";
  let a = 1;
  ```

- 常量

  ```
  const PI = 3.14;
  ```

##### 6 对象

- ```javascript
  var obj = new Object();
  obj = {
      name: "Simon",
      age: 20，
      email: 123@abc.com
      contact: {
      phone: 123456,
      Wechat: 123asd
  }
  };
  
  obj.contact.tele = "888"
  
  console.log(obj.contact);
  ```

##### 7 数组

- ```javascript
  var a = new Array();
  //空数组返回undefind
  ```

- for遍历和let in遍历

  ![image-20220209112322722](C:\Users\PHY\AppData\Roaming\Typora\typora-user-images\image-20220209112322722.png)![image-20220209112341072](C:\Users\PHY\AppData\Roaming\Typora\typora-user-images\image-20220209112341072.png)

  ```javascript
  for (let i in a){
  console.log(a[1]);
  }
  //let in方法输出时不会显示undefind所以更常用
  ```

##### 8 函数

- 声明：

  ```javascript
  function add(x){
  a += x;
  }
  
  add(4);
  
  console.log(a);
  ```

##### 9 闭包

- ```javascript
  function makeAdder(a){
      return function(b){  //好神奇！！
          return a + b;
      };
  }
  
  var x = makeAdder(5);
  var sum = x(6);
  
  console.log(sum);
  ```

  

#### 10 JavaScript漏洞

-   学什么？
  - 文件操作
  - HTML操作
  - DOM操作
  - Cookie操作
  - 数据操作

- 纯Javascript漏洞很多

- XSS
- docker搭建



### 11 系统学习

##### 0x00 输出语句

##### 1.alert()

```
alert（"XSS"）;
```

##### 2.document.write()

```
向body中输出一个内容
```

##### 3.console.log()

```
向控制台输出一个内容
```

##### 4.button

```javascript
<button onclick="alert('讨厌你点我干嘛');">点我一下</button>
```

##### 5.a href

```avascript
<a href="javascript:alert('让你点你就点！！');">你也点我一下</a>
```

##### 6.编写外部js文件并引入

```html
<script type="text/javascript" src="js/script.js"></script>;
//推荐使用方式
//script标签一旦用于引入外部文件了就不能再编写代码了
```

##### 7.Unicode编码

- console输出

  ```javascript
  console.log("\u0031");
  ```

- 在网页中使用Unicode编码

  ```html
  <h1>
      &#9760;  //注意网页中编码要转化为10进制
  </h1>
  ```

##### 8.代码块

```
代码块由{}分组，代码块中的语句要么一起执行要么都不执行
```

