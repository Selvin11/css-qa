> css-qa
1. [`position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);`怎么就实现了水平垂直居中？](#1)
2. [终结换行，属性全揭秘](#2)


<h4 id="1">1. position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);怎么就实现了水平垂直居中？</h4>

```css
.outer{
  position: relative;
  width:300px;
  height: 300px;
  background-color: #ccc;
}
.inner{
  position: absolute;
  top:50%;
  width:100px;
  height: 100px;
  transform: translateY(-50%);
  background-color: #999;
}

<div class="outer">
	<div class="inner"></div>
</div>
```

* `top:50%;`是根据outer的高度作为标准，即距离outer上边框150px
* `transform: translateY(-50%);`是根据inner本身的高度作为标准，即距离outer上边框-50px
* 因此两者结合起来inner刚好距离距离outer上边框150 - 50 = 100px，从而实现了垂直居中



<h4 id="2">2. 终结换行，属性全揭秘</h4>

* `white-space`:  设置如何处理元素内的空白，空白与换行符

  ```css
  white-space: normal;默认。空白会被浏览器忽略。
  white-space: pre;空白会被浏览器保留。其行为方式类似 HTML 中的 <pre> 标签。
  white-space: nowrap;文本不会换行，文本会在在同一行上继续，直到遇到 <br> 标签为止。
  white-space: pre-wrap;保留空白符序列，但是正常地进行换行。
  white-space: pre-line;合并空白符序列，但是保留换行符。
  white-space: inherit;规定应该从父元素继承 white-space 属性的值。
  ```

* `word-break`:  规定自动换行的处理方法，尤其是纯单词或字母时的换行

  ```css
  word-break: normal;	使用浏览器默认的换行规则。
  word-break: break-all; 允许在单词内换行 => 同时实现了word-wrap:break-word;长单词换行
  word-break:	keep-all; 只能在半角空格或连字符处换行。
  ```

* `word-wrap` :允许长单词或 URL 地址换行到下一行

  ```html
  <style> 
    word-wrap: normal;	只在允许的断字点换行（浏览器保持默认处理）。
    word-wrap: break-word;	在长单词或 URL 地址内部进行换行。

    p.test{
    width:11em; 
    border:1px solid #000000;
    word-wrap:break-word;
  }
  </style>

  <p class="test">This paragraph contains a very long word: thisisaveryveryveryveryveryverylongword.</p>
  // p.test的宽度固定为11em，但段落中有一个很长的单词，
  // 此时word-wrap:break-word;就可以让单词在定宽内换行
  ```