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

3. \$attrs  \$listeners inhertAttrs $parent