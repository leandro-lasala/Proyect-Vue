<template>
  <div>
    <h1>Mi primera app en vue</h1>
    <button @click="contador++">
    Clicks : {{contador}}
    </button>
  </div> 
</template>

<script setup>
import { ref } from 'vue'
const contador = ref(0)
</script>

<style scoped>
 button{
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
 }

</style>

