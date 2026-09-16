<template>
  大家好，我叫{{ name }}，今年{{ age }}岁，来自{{ address }},{{ msg  + 'world'}} 
</template>

<script setup>
import { ref } from 'vue'

const name = ref('张三')
const age = ref(18)
const address = ref('中国')
const msg = ref('hello') 

</script>

<style scoped>


</style>
