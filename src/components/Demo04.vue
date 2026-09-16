<template>
  {{ msg }}
  <input type="text" v-model="msg">
</template>


<script setup>
import { ref } from 'vue';

//MVVM模式,数据的双向绑定
//获取输入框的位置
//
//3.把1的值直接覆盖2
const msg = ref('hello vue')

</script>


<style scoped>


</style>