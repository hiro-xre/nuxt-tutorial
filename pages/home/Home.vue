<script setup lang="ts">
interface Member {
  id: number;
  name: string;
  email: string;
  points: number;
  note?: string;
}

const memberListInit = new Map<number, Member>();
memberListInit.set(33456, {id: 33456, name: "田中", email: "sample@sample.com", points: 35, note: "初回特典あり。"});
memberListInit.set(44783, {id: 44783, name: "鈴木", email: "sample2@sample2.com", points: 53});

const memberList = ref(memberListInit);

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
  <h1>Home Page</h1>
  <Sample />
  <section>
    <h1>会員リスト</h1>
    <p>全会員合計ポイント: {{ totalPoints }}</p>
    <OneSection
      v-for="[id, member] in memberList"
      :key="id"
      :id="id"
      :name="member.name"
      :email="member.email"
      v-model:points="member.points"
      :note="member.note"
    />
  </section>
</template>
