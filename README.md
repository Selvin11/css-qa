> css-qa
1. [`position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);`怎么就实现了水平垂直居中？](#1)


<h4 id="1">1. `position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);`怎么就实现了水平垂直居中？</h4>

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