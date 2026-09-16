<template>
  
  <div class ='box'>

    <h2>实验1：单向绑定(：value)</h2>
    <p>在输入框下打字，观察变化</p>
    <input type="text" :value="msg">
    <p>msg1: {{ msg }}</p>

    <hr> 
    
    <h2>实验2：双向绑定(：v-model)</h2>
    <p>在输入框下打字，观察变化</p>
    <input type="text" v-model="msg2">
    <p>msg2: {{ msg2 }}</p>
    <p style="color: orange;">msg2:实时同步 {{ msg2 }}</p>


    <hr> 

    <h2>实验3：手写v-model(:value和@input)</h2>
    <input type="text" :value="msg3" @input="msg3 = $event.target.value" placeholder="手写绑定">
    <p>msg3: {{ msg3 }}</p> 

  </div>

   


</template>

<script setup>
import { ref } from 'vue' 
//MVVM模式,数据的双向绑定
const msg1 = ref('初始值1')
const msg2 = ref('初始值2')
const msg3 = ref('初始值3')


</script>

<style scoped>
.box{
  width: 500px;
  height: 500px;
  border: 1px solid black;
  margin: 0 auto;
}
input{
  width: 300px;
  height: 30px;
}
</style>