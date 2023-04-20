<template>
  <div class="left-container">
    <h3 >Left 组件</h3>

    <hr >
    <!-- MyCount 已经 在 main.js 中 声明 为 全局组件 了， 所以 Left 组件 中 不用 再 导入 和 声明 了！  -->
    <!-- 通过 行内 属性， 使用 自定义 属性 init  -->
    <!-- 如果 init 前面 不加 冒号， 那么 init 是一个 字符串, 加 冒号 实质 上  是加   v-bind,   v-bind 中  的  内容  都是   js 。 js   中  单独  写一个  数字  是  number型的，  得加 单引号  （双引号）才是  字符串。  -->     
    <MyCount :init="9"  ></MyCount>


    <van-button type="primary">主要按钮</van-button>
  </div>

  
</template>

<script>
// import Count from '@/components/Count.vue'
export default {
  // Count 
  
}
</script>

<style lang="less" scoped >
.left-container {
  padding: 0 20px 20px;
  background-color: orange;
  min-height: 250px;
  flex: 1;
  
}
// 这是CSS选择器的写法，用于选择具有特定属性的HTML元素。

// 在这个选择器中，h3表示选择对应的元素为h3标签（即HTML中的标题3），中括号[]内的data-v-001则表示要选择具有data-v-001属性的h3元素。

// 简单来说，在HTML文档中，所有具有data-v-001属性的h3元素都会受到这个CSS规则的影响，实现文本颜色为红色。
h3 {
  color: red;
}
/deep/  h5 {
  color: pink;
}

</style>
