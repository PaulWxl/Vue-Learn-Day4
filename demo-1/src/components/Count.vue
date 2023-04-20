<template>
  <div id="app-container">
     <h5>Count 组件 </h5>


     <!-- 自定义 属性 props ， props: ['init'] , 所以 插值表达式 中  为  init  -->
     <p>count 的 值： {{ count }}</p>

     <!-- 如果方法 的 执行体 只有一行， 可以 不定义方法， 直接 写在 行内。   -->
     <!-- 注意：props 是只读的，不要直接修改 props 的值，否则终端会报错！ -->
     <!-- 注意， 千万不要写 init++, 控制台 会 报错， 不要 直接 修改 自定义 属性 。 已经 把 init 的 值  赋值  给  了  count，   就  让  count 自增，  count++     -->
     <button @click="count++">+1</button>
    <!-- 注意， 自己 不能 使用 自己 的 组件  -->
     <!-- <MyCount></MyCount> -->
  </div>
</template>

<script>
export default {
    // props 是 自定义属性， 允许 使用者 通过 自定义 属性 ， 为 当前 组件 指定 初始值。 
    // 不一定 非要叫 init， 合法 也可以。(不以数字开头) 
    // props 中的数据，可以直接在模板结构中被使用
    // 注意：props 是只读的，不要直接修改 props 的值，否则终端会报错！

    props: {
      // 自定义属性A : { /* 配置选项 */ },
      // 自定义属性B : { /* 配置选项 */ },
      // 自定义属性C : { /* 配置选项 */ },
      // 不一定 叫 init， 可以 自己 取。 比如: title  
      init: {
            // 用 default 属性定义 props 属性 的 默认值 
            // 如果外界使用 Count 组件的时候，没有传递 init 属性，则默认值生效
              default: 0,

              // 用 type 属性 定义 props 属性 的 值类型
              // 如果传递过来的值不符合此类型， 则会在终端报错
              // init 的值类型必须是 Number 数字
              // 常见的 类型 有： Boolean , String, Array, Object  
              type: Number,

              // 必填项校验
              // 只看 有没有 传递 这个 init  ， 而不是 看 有没有 初始值 ， 需要 做好 区分。 
              required: true

                }
            },


    data() {
      return {
         count: this.init
      }
    }
}



</script>

<style lang="less">

</style>