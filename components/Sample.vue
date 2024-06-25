<script setup lang="ts">
const count = ref(1)
const countUp = () =>{
  count.value++
}
</script>

<template>
  <button @click="countUp">increment</button>
  <p>{{ count }}</p>
</template>
