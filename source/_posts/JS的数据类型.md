---
title: JS的数据类型
date: 2018-06-29 16:46:57
tags:
---
JS有七种数据类型：number string boolean symbol undefined null object
注意：没有 array 类型也没有 function 类型。
## 一、number ##

 - 整数和小数（十进制）：1 : 1, 1.1 : 1.1, .1 : 0.1
 - 科学计数法：1.23e2 : 123
 - 二进制：0b11 : 3
 - 八进制：011 : 9（后来 ES5 添加了 0o11 语法）
 - 十六进制：0x11 : 17

## 二、string ##

 - 空字符串：''
 - 多行字符串：
   ```
   var s = '12345' +
              '67890' // 无回车符号
   或
   var s = `12345
   67890` // 含回车符号
   ```

## 三、boolean ##

 - 乔治·布尔
   乔治·布尔是英格兰数学家和哲学家、数理逻辑学先驱。
   由于其在符号逻辑运算中的特殊贡献，很多计算机语言中将逻辑运算称为布尔运算，将其结果称为布尔值。
   1864年，布尔冒着大雨步行两英里走到讲台，身着打湿的衣服为学生们授课。不久后，他就病倒了，得了重度感冒还发高烧。其妻错误地相信疾病需要用致病因子施救，因为布尔是淋雨水而感冒的，妻子于是用桶子装水淋到他身上。结果湿气进一步加剧了他的病情。1864年，12月8日，布尔死于肺部积水。
   上面资料的来源是维基百科，请自行选择是否相信。

 - boolean 的取值
   只有两个值：true 和 false
   a && b 在 a 和 b 都为 true 时，取值为 true；否则为 false
   a || b 在 a 和 b 都为 false 时，取值为 false；否则为 true

## 四、symbol ##
ES 6 引入了一个新的数据类型 Symbol

 - symbol的用途就是：Symbol 可以创建一个独一无二的值（但并不是字符串）。
 - symbol的作用：Symbol 生成一个全局唯一的值。
   [symbol是什么][1]

## 五、undefined 和 null ##
都表示没有值，至于 JS 为什么有两个表示「没有值」的东西，可以从 JS 之父的 twitter 中知道当时他也挺纠结的：https://twitter.com/BrendanEich/status/333008305461006336

 - undefined：（规范）如果一个变量没有被赋值，那么这个变量的值就是 undefiend

 - null：（习俗）如果你想表示一个还没赋值的对象，就用 null。

 - 如果你想表示一个还没赋值的字符串/数字/布尔/symbol，就用 undefined（但是实际上你直接 var xxx 一下就行了，不用写 var xxx = undefined）
一般来说null表示空对象，undefined表示空非对象

## 六、object ##
除了object其他都是基本类型，object是复杂类型

 - object 就是上面几种基本类型（无序地）组合在一起
 - object 里面可以有 object
   ```
    var person = {
      name: 'Frank', 
      'child': {
          name: 'Jack'
      }, // 最后这个逗号可有可无
  }
   ```
 - object 的 key 一律是字符串，不存在其他类型的 key
 - object[''] 是合法的
 - object['key'] 可以写作 object.key
 - 注意 object.key 与 object[key] 不同
 - delete object['key']
 - 'key' in object
 - for(var key in object)

## 七、typeof 操作符 ##
typeof可以用来判断数据类型，但是存在两个bug
 - typeof null的类型为'object'
 - typeof function的类型为'function',但是并没有function数据类型

  [1]: https://zhuanlan.zhihu.com/p/22652486