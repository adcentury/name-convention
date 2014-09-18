命名规则
===============

- [概述](#user-content-%E6%A6%82%E8%BF%B0)
- [说明](#user-content-%E8%AF%B4%E6%98%8E)
- [HTML](#user-content-html)
		- [class属性](#user-content-class%E5%B1%9E%E6%80%A7)
		- [id属性](#user-content-id%E5%B1%9E%E6%80%A7)
		- [data属性（自定义属性）](#user-content-data%E5%B1%9E%E6%80%A7%E8%87%AA%E5%AE%9A%E4%B9%89%E5%B1%9E%E6%80%A7)
- [Javascript](#user-content-javascript)
		- [常量](#user-content-%E5%B8%B8%E9%87%8F)
		- [类](#user-content-%E7%B1%BB)
		- [普通变量&函数](#user-content-%E6%99%AE%E9%80%9A%E5%8F%98%E9%87%8F%E5%87%BD%E6%95%B0)
		- [Jquery对象](#user-content-jquery%E5%AF%B9%E8%B1%A1)

# 概述

本篇文档用于统一命名规则，以便于协同合作和提升工作效率。

# 说明

# HTML

### class属性

* 使用 __-（短横杠）__ 作为单词分割

* `class="<word1>[-word2][-word3]..."`

```html
<!-- class属性命名示例 -->
<div class="one"></div>
<div class="two-words"></div>
<div class="class-name-with-multiple-words"></div>
```

### id属性
* 使用 __-（短横杠）__ 作为单词分割

* `id="<word1>[-word2][-word3]..."`

```html
<!-- id属性命名示例 -->
<span id="id"></span>
<span id="two-words"></span>
<span id="id-name-with-multiple-words"></span>
```

### data属性（自定义属性）

* 使用 __-（短横杠）__ 作为单词分割

* `data<-word1>[-word2][-word3]...`

```html
<!-- data属性命名示例 -->
<div
  id="example"
  data-role="page"
  data-last-value="11"
  data-hidden="true"
  data-options='{"key": "value"}'>
</div>
```

>提示：data属性可以通过Jquery，Javascript或者CSS访问

>Jquery示例 ([.data() | jQuery API Documentation](http://api.jquery.com/data/))

>```javascript
$('#example').data('role') === 'page'  // true
$('#example').data('lastValue') === 11  // true
$('#example').data("hidden") === true  // true
$('#example').data('options').key === 'value'  // true
```

>Javascript示例([Using data attributes - Web developer guide | MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_data_attributes))

>```javascript
var example= document.querySelector('#example');

>example.dataset.role  // 'page'
example.dataset.lastValue // '11'
example.dataset.hidden  // 'true'
example.dataset.options  // '{"key":"value"}'
```

>*注意：使用dataset得到的所有值均为字符串

>CSS示例([Using data attributes - Web developer guide | MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_data_attributes))

>```css
#example::before {
  content: attr(data-parent);
}
div[data-role='page'] {
  width: 400px;
}
div[data-hidden='true'] {
  display: none;
}
```

# Javascript

>说明1：由于Javascript是基于原型的语言，所以下述分类并不代表真实类型，仅为约定俗成

>说明2：以下划线(_)开头的命名方式被保留，用作后续需求

### 常量

* 使用 __全大写字母__

* 使用 __下划线(_)__ 作为单词分割

* `var <WORD1>[_WORD2][_WORD3]...`

```javascript
// 常量命名示例
var IMMUTABLE = 'my heart';
var THE_ONE_TO_BE_WITH = 0;
var COMMON_CONST = JW_COMMON_CONST || {
  FOO: 'belongs to you',
  BAR: 1,
  ...
};
```

### 类

* 使用 __驼峰式__ 命名规则([CamelCase - Wikipedia, the free encyclopedia](http://en.wikipedia.org/wiki/CamelCase))

* 第一个单词需使用 __大写字母__ 开头

* `var <Word1>[Word2][Word3]...`

```javascript
// 类命名示例
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
}
Person.prototype.meet = function(anotherPerson, place) {
  var ret = '';
  if(this.gender === anotherPerson.gender) {
    ret = 'On My God!';
  } else {
    ret = this.name + ' meet ' + anotherPerson.name + ' at ' + place;
  }
  return ret;
}

var adam = new Person('Adam', 'male');
var eve = new Person('Eve', 'female');
var god = new Person('God', 'male');

alert(adam.meet(eve));
alert(adam.meet(god));
```

### 普通变量&函数

* 使用 __驼峰式__ 命名规则

* 第一个单词需使用 __小写字母__ 开头

* `var <word1>[Word2][Word3]...`

  `function <word1>[Word2][Word3]...`

```javascript
// 普通变量&函数命名示例
var num = 11;
var myText = 'Hello World.';
var strThatYouMustUseManyWordsToExplain = 'too short';
var anObject = {};
var anArray = [];

function rock() {}
function rockMyLife(data, localVariable) {}

var resultFromFunction = rock();
var resultFromJQueryHelper = $.trim('       Do you love me?        ');
```

### Jquery对象

说明：对Jquery对象进行单独规定目的在于便于区分，即提醒阅读者此变量来自 `$()` 函数返回

* 使用 __驼峰式__ 命名规则

* 以 __$符号__ 作为开头

* `var $<word1>[Word2][Word3]...`

```javascript
// Jquery对象命名示例
var $node = $('#node');
var $allLinks = $('.links');
var $returnOfMostJqueryObjectFunctionIsAlsoJqueryObject = $('#if-you-dont-love-me').fadeOut('fast');
```
