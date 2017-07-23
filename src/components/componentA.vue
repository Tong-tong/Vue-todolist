<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>{{ msgfromfather }}</h3>
    <button v-on:click="clickme">click</button>
  </div>
</template>

<script>
    export default {
     
      data:function() {
        return{

          msg: 'Welcome to Your Vue.js App and component a'
        }
          
        },
        props:['msgfromfather'],   //增加父元素属性
        methods:{
          clickme:function(){
            console.log(this.msgfromfather)
          }
        }
      
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
      h1, h2 {
        font-weight: normal;
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
