<template>
  <div class="right-container" >
    <h3 >Right 组件</h3>
    <hr >
    <!-- 通过 行内 属性， 使用 自定义 属性 init  -->
    <MyCount :init="6"  ></MyCount>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less" scoped>
.right-container {
  padding: 0 20px 20px;
  background-color: lightskyblue;
  min-height: 250px;
  flex: 1;
}
h3 {
  color: #6c99c5;
}
h5 {
  color: pink;
}
</style>
