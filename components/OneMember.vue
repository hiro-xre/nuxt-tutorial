<script setup lang="ts">
import type { Member } from '@/interface';

interface Props {
  id: number;
}

const props = defineProps<Props>();

const memberList = useState<Map<number, Member>>("memberList");
const member = memberList.value.get(props.id) as Member;

const localNote = computed(
  (): string => {
    let localNote = member.note;
    if(localNote == undefined) {
      localNote = "--";
    }
    return localNote;
  }
)

const pointUp = (): void => {
  member.points++;
}
</script>

<template>
  <section class="box">
    <h4>{{ member.name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>{{ id }}</dd>
      <dt>メアド</dt>
      <dd>{{ member.email }}</dd>
      <dt>保有ポイント</dt>
      <dd>{{ member.points }}</dd>
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
