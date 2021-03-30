# css设置元素固定长宽比自适应父元素

**知识点：  垂直方向上当内外边距使用百分比做单位时，是基于包含块当宽度来计算的**

```
// 图片等比例自适应
<ul class="all">
    <li class="card">
        <div class="img-box">
            <img class="image">
        </div>
    </li>
</ul>

<style>
.all {
    width: 100%;
    height: auto;
}
.card {
    width: calc(100% / 4 - 20px);
    height: auto;
    position: relative;
}
.img-box {
    width: 100%;
    height: 0px;
    padding-bottom: 61.8%; // 高度
}
.image {
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0px;
    left: 0px;
}
</style>
```

