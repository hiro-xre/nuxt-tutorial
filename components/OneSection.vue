<script setup lang="ts">
interface Props {
  id: number;
  name: string;
  email: string;
  points: number;
  note?: string;
}

interface Emits {
  (event: "incrementPoint", id: number): void;
}

const props = defineProps<Props>();
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

const pointUp = (): void => {
  emit("incrementPoint", props.id);
}
</script>

<template>
  <section class="box">
    <h4>{{ name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>{{ id }}</dd>
      <dt>メアド</dt>
      <dd>{{ email }}</dd>
      <dt>保有ポイント</dt>
      <dd>{{ points }}</dd>
      <dt>備考</dt>
      <dd>{{ localNote }}</dd>
    </dl>
    <button @click="pointUp">ポイントアップ</button>
  </section>
</template>

<style>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>
