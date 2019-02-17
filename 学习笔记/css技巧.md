
### 常见技巧

1. 单侧投影

   ```scss
   // 利用扩张半径将另一边投影收进去
   box-shadow: -7px 0 5px -5px #333;
   ```

2. 瀑布流

   >瀑布流每行内容行高不一致 有错落感，所以float 内联盒子都无法实现,可以用flex实现，**水平平分每一列,然后每一列竖直排列**

3. 跨行跨列布局

   >利用float特性 :同行元素如果没有**超出最大行高（最高的那个元素撑起的行高）**则会换行紧接着第一个元素排列  

4. 多列等高方案（常用于侧边栏等布局）

   1. padding+margin

      > 利用元素 默认的background-clip是padding-box 所以即便用margin将无限大的padding抵消掉了 但是背景依然显示，所以将会出现 左侧元素实际大小并没有等高于右侧元素，但是背景显示等高于右侧

5. 立体文字投影

   > 立体文字阴影的关键点在于多层 text-shadow 的叠加
   >
   > 利用scss函数进行计算层级阴影颜色

   ```scss
   @function makelongrightshadow($color) {
       $val: 0px 0px $color;
       @for $i from 1 through 50 {
           $color: fade-out(desaturate($color, 1%), .02);
           $val: #{$val}, #{$i}px #{$i}px #{$color};
       }
       @return $val;
   }
   
   @function makelongleftshadow($color) {
       $val: 0px 0px $color;
       @for $i from 1 through 50 {
           $color: fade-out(desaturate($color, 1%), .02);
           $val: #{$val}, -#{$i}px #{$i}px #{$color};
       }
       @return $val;
   }
   
   div {
       text-align: center;
       font-size: 20vmin;
       line-height: 45vh;
       text-shadow: makelongrightshadow(hsla(14, 100%, 30%, 1));
       color: hsl(14, 100%, 60%);
   }
   
   .left {
       text-shadow: makelongleftshadow(hsla(231, 50%, 30%, 1));
       color: hsl(231, 50%, 60%);
   }
   ```

   ![image-20190213214121602](/Users/adamvijay/Documents/markdown_笔记/学习笔记/assets/image-20190213214121602.png)

   

6. 弹窗背景模糊（虚化背景）

> 利用:not()伪类，将除弹窗外的所有子元素虚化

```scss
.c-box {
    background: #ccc;
    width: 100px;
    height: 100px;
    padding: 20px;
    border: 20px solid transparent;
    background-clip: padding-box;
}
.c-dialog {
    height: 30px;
    text-align: center;
    background: #1a98cc;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
.c-box-wrap {
    width: min-content;
    position: relative;
    & > :not(.c-dialog) {
        filter: blur(2px);
    }
}
```

7. 三角形实现

   ```scss
   .arrow {
       display: inline-block;
       border: 10px solid transparent;
       border-bottom-color: #ccc;
   }
   ```

8. 渐变实现斜条纹

   1. 颜色需要对称 即`45deg,#000 0,#000 25%,yellow 25% ,yellow 50%,#000 50%,#000 75%,yellow 75% ,yellow 100%` **0~50 50~100内的区间段需要一致**，或者使用`repeating-linear-gradient`，可以简写为`repeating-linear-gradient(45deg,#000 0,#000 25%,yellow 25% ,yellow 50%)` **自动会补全对称**
   2. `background-size: 20px 20px;` 背景高度宽度需要一致
   3. 角度必须为45的倍数

   ```scss
   .progress {
       height: 20px;
       background:repeating-linear-gradient(45deg,#000 0,#000 25%,yellow 25% ,yellow 50%);
       background-size: 20px 20px;
   }
   ```

9. 径向渐变实现优惠券

   ```scss
   &::before {
       width: 10px;
       background-image: radial-gradient(circle at -5px 10px, transparent 12px, #fff 13px, #fff 0px);
       background-size: 20px 20px;
       background-position: 0 15px;
   }
   
   &::after {
       width: 15px;
       background-image: radial-gradient(circle at 15px 10px, #fff 12px, transparent 13px, transparent 0px);
       background-size: 20px 40px;
       background-position: 0 15px;
   }
   ```

10. 使用`z-index + background:inherit`实现毛玻璃

    > background:inherit**会直接继承父容器对应自容器位置的背景**，当毛玻璃容器继承背景后，**再让它的伪元素继承背景，让伪元素虚化作为毛玻璃背景**，再让内容元素的z-index大于伪元素背景
    >
    > 注意：**相对定位也可以设置z-index**，使用相对定位可以占据文档流，使父容器可以跟随当前内容变化

```scss
#app {
    height: 200px;
    line-height: 200px;
    text-align: center;
    background: url("https://images.unsplash.com/photo-1440688807730-73e4e2169fb8?dpr=1&auto=format&fit=crop&w=1500&h=1001&q=80&cs=tinysrgb&crop=");
    .dialog-wrapper {
        position: relative;
        display: inline-block;
        background: inherit;
        &:after {
            position: absolute;
            content: "";
            background: inherit;
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
            filter: blur(20px);
        }
    }
    .dialog {
        display: inline-block;
        padding: 60px;
        position: relative;
        z-index: 10;
        color: wheat;
    }

}
```

11. 波浪动画

    > 要点:
    >
    > 填充主颜色，after before重叠，并为另外两个颜色，将after before 动画时间 圆角 错落开 错落的颜色就形成了波浪
    >
    > tips: animation-delay可以设置为负数，以方便提前产生错落

    ```scss
    .wave {
        position: relative;
        width: 200px;
        height: 200px;
        background-color: rgb(118, 218, 255);
        margin: 200px;
        overflow: hidden;
        &::before,
        &::after{
            content: "";
            position: absolute;
            width: 400px;
            height: 400px;
            top: 0;
            left: 50%;
            background-color: rgba(201, 211, 255, 0.4);
            border-radius: 45%;
            transform: translate(-50%, -70%) rotate(0);
            animation: rotate 6s linear infinite;
            z-index: 10;
        }
    
        &::after {
            border-radius: 47%;
            background-color: rgba(255, 255, 255, .9);
            animation: rotate 10s linear -5s infinite;
            z-index: 20;
        }
    }
    
    @keyframes rotate {
        50% {
            transform: translate(-50%, -73%) rotate(180deg);
        } 100% {
            transform: translate(-50%, -70%) rotate(360deg);
        }
    }
    ```

    