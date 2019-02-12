### 瀑布流

> 难点:瀑布流每行内容行高不一致 有错落感，所以float 内联盒子都无法实现
>
> 下面使用flex实现

<p class="codepen" data-height="265" data-theme-id="0" data-default-tab="css,result" data-user="vijayniubi" data-slug-hash="QYamzO" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid black; margin: 1em 0; padding: 1em;" data-pen-title="flex瀑布流">
  <span>See the Pen <a href="https://codepen.io/vijayniubi/pen/QYamzO/">
  flex瀑布流</a> by Vijay (<a href="https://codepen.io/vijayniubi">@vijayniubi</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

### 跨行跨列布局

> 利用float特性 :同行元素如果没有**超出最大行高（最高的那个元素撑起的行高）**则会换行紧接着第一个元素排列

<p class="codepen" data-height="265" data-theme-id="0" data-default-tab="css,result" data-user="vijayniubi" data-slug-hash="QYarjr" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid black; margin: 1em 0; padding: 1em;" data-pen-title="跨行跨列布局">
  <span>See the Pen <a href="https://codepen.io/vijayniubi/pen/QYarjr/">
  跨行跨列布局</a> by Vijay (<a href="https://codepen.io/vijayniubi">@vijayniubi</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>



### 多列等高方案（常用于侧边栏等布局）

1. padding+margin

   > 利用元素 默认的background-clip是padding-box 所以即便用margin将无限大的padding抵消掉了 但是背景依然显示，所以将会出现 左侧元素实际大小并没有等高于右侧元素，但是背景显示等高于右侧

   <p class="codepen" data-height="265" data-theme-id="0" data-default-tab="css,result" data-user="vijayniubi" data-slug-hash="xMpjNE" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid black; margin: 1em 0; padding: 1em;" data-pen-title="多列等高">
     <span>See the Pen <a href="https://codepen.io/vijayniubi/pen/xMpjNE/">
     多列等高</a> by Vijay (<a href="https://codepen.io/vijayniubi">@vijayniubi</a>)
     on <a href="https://codepen.io">CodePen</a>.</span>
   </p>
   <script async src="https://static.codepen.io/assets/embed/ei.js"></script>

2. flex

    

### flex相关

1. flex:1简写如下

   ```scss
   flex-grow: 1; //每个项占有容器的面积比例
   flex-shrink: 1; //当项超出容器时缩放的比例 0为不缩放
   flex-basis: 100%; //当项小于容器时放大的比例
   ```

   