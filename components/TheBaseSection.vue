<script setup lang="ts">
import type { Member } from '@/interface';

const memberList = useState<Map<number, Member>>("memberList");

const totalPoints = computed(
  (): number => {
    let total = 0;
    for(const member of memberList.value.values()) {
      total += member.points
    }
    return total;
  }
)
</script>

<template>
  <section>
    <h1>会員リスト</h1>
    <p>全会員合計ポイント: {{ totalPoints }}</p>
    <OneMember
      v-for="id in memberList.keys()"
      :key="id"
      :id="id"
    />
  </section>
</template>

<style>
section {
  border: orange 1px solid;
  margin: 10px;
}
</style>
