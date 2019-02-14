1. vue具名插槽 slot

   ```vue
   //父组件
   <test-cmp>
       <template slot="body" slot-scope="{data}">
   <div>{{data}}</div>
       </template>
   </test-cmp>
   
   //子组件
   <div id="TestCmp">
       <slot name="body" :data="name"/>
   </div>
   ```

   `注意：slot的name属性已被具名占用，所以不得使用name传递属性`

2. 指令

   1. update`v-show触发`
   2. bind`v-if触发`
   3. insert`v-if触发`
   4. unbind`v-if触发`
   5. **仅更改属性时触发update,移除或添加元素时触发其他钩子**
   6. 钩子函数参数
      1. el元素
      2. binding 绑定的相关
      3. vnode 当前组件的虚拟节点
      4. oldVnode 上一个状态的虚拟节点

3. \$attrs  \$listeners inhertAttrs $parent

1. mvvm实现
2. 虚拟dom
3. 双向绑定
4. vue-router实现
5. 作用域链
6. vue生命周期