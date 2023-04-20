
<template>
  <div class="app-container">
    <h1>App 根组件 </h1>

    <button @click="flag = !flag">Toggle Flag</button>
    <!-- 加一个v-if 意思就是 如果 flag为 true， 那么 就 保留 Test 组件， 否则 就 删除 Test 组件。 检查 beforeDestroy 函数。  -->
    <Test info="你好" v-if="flag"></Test>
    <hr>
    
    <div class="box">
        <!-- 渲染 Left 和 Right 组件  -->

        <!--在 template 中   用 标签  的 形式 使用  注册 的 组件 ， <import 接受 的 名称 ></import 接受 的 名称 >    -->
        <!-- 可以 看做 是 自定义 标签  -->
        <!-- 标签名 要 和 import 接受 名称 一致  -->
        <Left></Left>
        <Right></Right>
    </div>
    
  </div>
</template>

<script>

// 先 导入 子组件 ， @ 已经 被 vue-cli 自动 配置 好了， 默认 指向 ./src , 可以 直接 使用。
// 导入 需要 使用 的 .vue 组件  
import Left from '@/components/Left.vue'
import Right from '@/components/Right.vue'
import Test from '@/components/Test.vue'

export default {


    // 在 components 节点 下， 注册 组件， 写 的 是 import 接受 的 名称 
    components: {
      // 声明 组件 
      // 在 对象 里面， 如果 键 和 值 一样， 可以 省略 键
      // 完整写法 ： 
      // 'Left': Left
      // 'Right': Right

      // 底下 这种 是 简写 形式 , 这个 声明 的 名称 是 import 接受 的 名称值 
      // 多个 组件 的 注册 用 逗号 分隔 
        Left,
        Right,
        Test 
    },
    data() {
       return {
          flag: true
       }
    },
    methods: {
       
    }

}
</script>

<style lang="less">
.app-container {
  padding: 1px 20px 20px;
  background-color: #efefef;
}
.box {
  display: flex;
}
</style>
