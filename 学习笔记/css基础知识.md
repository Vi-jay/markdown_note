### 基础知识

1. ie盒模型和标准盒子模型区别:

   1. ie盒模型是 content +padding+border 即:border-box
   2. 标准盒模型是 content 即:content-box
   3. 盒子模型由margin padding content border组成

2. background-attachment

   1. fixed 内容滚动，背景固定
   2. scroll 内容滚动，背景跟随滚动`默认`

3. text-indent 文本缩进

4. background-position

   1. 可以使用 left right 来指定背景紧贴位置
   2. 可以使用 left  10px right 10px 来指定紧贴位置间距
   3. 可以指定 10px 10px 默认是 从left top计算

5. 媒体查询（响应式）

   ```css
   @media screen and (max-width:800px) /*当宽度小于800时应用*/
   @media screen and (min-width:800px) /*当宽度大于800时应用*/
   ```

6. align-content

   > 在**多行**的情况下使用，效果与align-items相同

7. animation

   ```Scss
   animation: rotate 2s linear 3;
   animation-fill-mode: forwards;
   //最终状态 forwards保持最终状态 backwards保持最初状态
   animation-direction: alternate;
   //运行方式 alternate为顺时针一次 逆时针一次
   animation-iteration-count: 3;
   //运行次数
   ```

   

8. background-clip

   > 默认是border-box,即背景从边框底下开始显示

9. flex相关

   ```scss
   flex-grow: 1; //每个项占有容器的面积比例
   flex-shrink: 1; //当项超出容器时缩放的比例 0为不缩放
   flex-basis: 100%; //当项小于容器时放大的比例
   ```

10. flex**横向排列时会将每个项的高度自动铺满**，不要手动设置height:100%;因为 如果父容器的高度是又某个项撑起的话 **那父容器是没有尺寸高度的**，那么height:100%反而会不现实高度

