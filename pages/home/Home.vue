<script setup lang="ts">
const randInit = Math.round(Math.random() * 10);
const rand = ref(randInit);
const onCreateNewRand = (): void => {
  rand.value = Math.round(Math.random() * 10);
}
</script>

<template>
  <h1>Home Page</h1>
  <Sample />
  <section>
    <p>親で乱数を表示</p>
    <OneSection
      :rand="rand"
      v-on:createNewRand="onCreateNewRand"
    />
  </section>
</template>
