<script setup lang="ts">
interface Props {
  rand: number;
}

interface Emits {
  (event: "createNewRand"): void;
}

defineProps<Props>();
const emit = defineEmits<Emits>();

const onNewRandButtonClick = (): void => {
  emit("createNewRand");
}
</script>

<template>
  <section class="box">
    <p>子の乱数を表示:{{ rand }}</p>
    <button @click="onNewRandButtonClick">乱数を生成</button>
  </section>
</template>

<style>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>
