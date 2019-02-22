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

3. 内置对象

   1. \$attrs 如果组件定义了props，那么其他没被定义的属性都会在$attrs内置对象中
   2. $props 所有父组件传递的props，只能获取到定义的prop
   3. \$listeners `v-on="$listeners"`传递事件监听时使用
   4. inhertAttrs  默认情况下所有非props属性都会绑定到元素上作为元素属性，如果设置这个行为为false则不会绑定
   5. $parent 获取到父组件实例，可以调用函数等

4. 虚拟dom

   1. 虚拟DOM的存在的意义？vdom 的真正意义是为了实现跨平台，服务端渲染，以及提供一个性能还算不错 Dom 更新策略。vdom 让整个 mvvm 框架灵活了起来

5. 双向绑定

   > 利用DocumentFragment劫持目标DOM的子元素，然后操作被劫持DocumentFragment里的子元素，最后将DocumentFragment替换原DOM，完成批量DOM操作

   1. Object.defineProperty进行监听数据的getset
   2. 在vue初始化时 使用DocumentFragment编译HTML，绑定指令和{{}}
   3. 使用发布者/订阅者模式 将发布者相关的属性(例如v-bind)进行订阅，在v-model绑定的元素事件中进行发布

6. vue-router实现

   1. history模式是采用pushState popState + onpopstate事件组成的
   2. hash模式是采用 onhashchange事件组成

7. vue生命周期

   1. create->mount->update->destory

8. 纯组件（无状态组件,无法注入其他组件）

   1. 在tamplate上设置functional属性即可，或者在实例属性上设置functional:true

9. 动态渲染组件

   ```vue
   <span :is="cmpName">
       asd
   </span>
   <script>
       components: {UnderlineText, Test2},
       data() {
           return {
               cmpName: "underline-text"
           }
       }
   </script>
   ```

10. provide,inject

    > 提供了跨组件调用祖先实例api的能力

    ```vue
    //parent
    provide() {
        return {
        changeMsg: this.changeMsg
        }
    }
    
    //child
    inject:["changeMsg"]
    <button @click="changeMsg('msg')">btn</button>
    
    ```

11. [animate.css动画库使用](https://www.w3cplus.com/vue/vue-animation.html)

