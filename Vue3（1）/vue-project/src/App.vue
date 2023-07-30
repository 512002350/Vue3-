<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>父组件中接收到的数据:{{ childData}}</h1>
    <button  @click = 'parentCount++'>{{ parentCount}}</button>
    <HelloWorld
      msg="Welcome to Your Vue.js App"
      :count = 'parentCount'
      @child-count-change = 'handler'
      >
      这是默认内容1
      <template v-slot:footer = "{dataObj}">第一个footer{{ dataObj}}</template>
    </HelloWorld>
      <!-- 由父组件引入子组件，因此在父组件里用html标签来表示这个组件，
      里面的msg后接的值用于传递给子组件 -->
      <!-- 数据名前加冒号：目的在于把数据变成响应式数据 -->
      <!-- 这是子组件自己定义的一个事件，由父组件进行监听 -->
    
    
    <HelloWorld>这是默认内容2</HelloWorld>
    <HelloWorld>这是默认内容3</HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data(){
    return{
      parentCount:1000,
      childData:0
    }
  },
  components: {
    HelloWorld
  },
  methods:{
    handler (childCount) {
      this.childData=  childCount
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
