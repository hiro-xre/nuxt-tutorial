<script setup lang="ts">
interface Emits {
  (event: "update:points", points: number): void;
}

const emit = defineEmits<Emits>();

const localNote = computed(
  (): string => {
    let localNote = props.note;
    if(localNote == undefined) {
      localNote = "--";
    }
    return localNote;
  }
)

const onInput = (event: Event): void => {
  const element = event.target as HTMLInputElement;
  const inputPoints = Number(element.value);
  emit("update:points", inputPoints);
}
</script>

<template>
  <section class="box">
    <h4>{{ name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>
        <input type="number" :value="points" v-on:input="onInput">
      </dd>
      <dt>メアド</dt>
      <dd>{{ email }}</dd>
      <dt>保有ポイント</dt>
      <dd>{{ points }}</dd>
      <dt>備考</dt>
      <dd>{{ localNote }}</dd>
    </dl>
  </section>
</template>

<style>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>
