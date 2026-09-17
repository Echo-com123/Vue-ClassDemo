<template>
  <img v-bind:src="img" alt="Hero Image">

<p v-bind:class="a">这是一个英雄图片</p>

<!-- v-on @ -->
 
 <button v-on:click="onclick">点击我</button>
</template>


<script setup>
import url1 from '../assets/hero.png'
const img = url1

const a = 'a'

const onclick = () => {
  alert('你点击了按钮')
}


</script>

<style scoped>
img{
  width: 200px;
  height: 200px;
}

.a{
  color: rgb(151, 29, 29);
}

</style>
