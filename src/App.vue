<template>
  <div id="app">
    <h1 v-text="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">

        {{item.label}}
      </li>
    </ul>
<!-- 父元素传给子元素的话,ComponentA要转为小写并用'-'隔开 -->
    <component-a msgfromfather='father said'></component-a>  

  </div>
</template>

<script>
import Store from './store'  //引入Store存储文件
import ComponentA from './components/componentA'    //引入子文件

export default {
    data:function(){
    return{
       title:'this is a todu list',
       items:Store.fetch(),   //存储
       newItem:''   
    } 
  },
  methods:{
    toggleFinish:function(item){
     item.isFinished = !item.isFinished
    },

    addNew:function(){
          this.items.push({
          label:this.newItem,
          isFinished:false
      })
      this.newItem=''   //回车后输入框清空
    }
  },

components:{ComponentA},    //引入ComponentA文件后要注册才可用

  watch:{
    items:{
      handler:function(items){
          Store.save(items)
      },
      deep:true
    }
  }
}
</script>

<style>
.finished{
  text-decoration: underline;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
