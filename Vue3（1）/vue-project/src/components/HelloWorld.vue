<template>
  <div class="hello">
    <slot>基础默认内容</slot>
    <!-- 插槽 -->
    <!-- 这是在用单标签使用组件的时候会显示的文字 -->
    <!-- 若是用双标签使用组件的话可以自定义显示内容 -->
    <!-- 除了通过 props 传递数据外，父组件还可以通过插槽 (slots) 将模板片段传递给子组件： -->
    <!-- 在子组件中，可以使用 <slot> 元素作为插槽出口 (slot outlet) 渲染父组件中的插槽内容 (slot content)： -->
    <!-- <slot> 插口中的内容将被当作“默认”内容：它会在父组件没有传递任何插槽内容时显示： -->
      <h1>{{ msg }}</h1>
    <p>props中的count{{count}}</p>
    <button @click="handler()">按钮</button>
    <slot name="footer" :childCount = 'childCount'>footer的默认内容</slot>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  // 组件通信
  // 1、父传子  props
  // 2、子传父  $emit()
  // 3、同级传递  同属于一个父组件，所以可以把子组件的值传给父组件，再从父组件传给子组件
  // 4、若出现两个组件当中隔了很多层的关系的话，建议使用vuex
  props: {
    msg: String,
    count:{
      type:[String,Number],
      // default:100
      // required: true
    }
  },
  data(){
    return{
      childCount:0
    }
  },
  methods:{
    handler(){
      this.childCount++;
      this.$emit('child-count-change',this.childCount)
      // $emit() 可以触发自定义事件，每次触发'child-count-change'，就传递this.childCount
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
