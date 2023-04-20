<template>
  <div class="test-container">
    <h3 id="myh3" >Test.vue  组件 ---- {{ books.length }} 本图书</h3>
    <p>message 的值： {{ message }}</p>
    <button @click="message += '~'">修改message的值</button>
  </div>
</template>

<script>
export default {
  props: ['info'],
  data() {
    return {
      message: 'hello vue.js',
      // 定义 books 数组， 存储的是 所有 图书 列表 数据 ， 初始化 为 空数组。 
      // 先在data 中 定义了 一个 空数组 books， 然后 当 result 有 结果 时， 就 把底下的 data 属性（data 是 一个 数组）， 赋值   给  books， 那么 books 就不再是  一个  空数组了，  然后 直接 把 books.length 渲染到  页面  中 就行了。 {{ books.length }}
      books: [],
    }
  },
  methods: {
    show() {
      console.log('调用了 Test 组件 的  show 方法 ')
    },
    // 使用 ajax 请求 图书列表 的 数据
    initBookList() {
      // 用 原生 去 发 ajax 请求
      const xhr = new XMLHttpRequest
      xhr.addEventListener('load', () =>  {
        // 从服务器 返回 的 数据 是 JSON 格式的， 需要 转换为 对象
        const result = JSON.parse(xhr.responseText)
        // console.log(result)
        // 先在data 中 定义了 一个 空数组 books， 然后 当 result 有 结果 时， 就 把底下的 data 属性（data 是 一个 数组）， 赋值   给  books， 那么 books 就不再是  一个  空数组了，  然后 直接 把 books.length 渲染到  页面  中 就行了。 {{ books.length }}
        this.books = result.data
      })
      // 然后 该open，send 了
      // open : 初始化 一个 HTTP 请求
      xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks')
      // send : 发送 这个 HTTP 请求
      xhr.send()

    }

  },
  // 定义 创建阶段 的  第一个 生命周期函数
  beforeCreate() {
    //console.log(this.info)// 不可用
    //console.log(this.message)// 不可用
    //this.show()// 不可用
  },
  // 定义 创建阶段 的  第二个 生命周期函数
  created() {
    // console.log(this.info)// 可用
    // console.log(this.message)// 可用
    // this.show()// 可用
    // this.initBookList()
    // const dom = document.querySelector('#myh3')
    // console.log(dom)// null --- 说明 created阶段 模板结构 还没有 被 渲染
  },
  beforeMount() {
    // console.log('beforeMount')
    // const dom = document.querySelector('#myh3')
    // console.log(dom)// null --- 说明 beforeMount阶段 浏览器 中 还没有 当前 组件 的 DOM 结构 ， 不能 操作 组件 的 DOM 结构 
    // console.log(this.$el)// undefined
  },
  mounted() {
    // console.log(this.$el)// 可以 打印 出 template 中 的 UI 结构， 说明 mounted 时， 组件 中 UI 结构 已经 被 渲染 到 浏览器 页面 上了。 所以， 浏览器 可以 操作 组件 中 的 DOM 结构 了。 

    // const dom = document.querySelector('#myh3')
    // console.log(dom)
  },
  beforeUpdate() {
    // console.log('触发了 beforeUpdate 生命周期函数。 ');// 第一次 会 触发 是因为 前面的 initBooks 中  books 更改了，books 也是 data 里面 的 值。
    // console.log(this.message)
    // const p = document.querySelector('p')
    // console.log(p.innerHTML)
  },
  updated() {
    // console.log('触发了 updated 生命周期函数。 ');
    // console.log(this.message)
    // const p = document.querySelector('p')
    // console.log(p.innerHTML)
  },

  beforeDestroy() {
    console.log('使用了 beforeDestroy 生命周期函数')
    console.log(this.message)
  },

  destroyed() {
    console.log('使用了 destroyed  生命周期函数')
  }

}
</script>

<style>
    .test-container {
        background-color: pink;
        height: 200px;
    }
</style>