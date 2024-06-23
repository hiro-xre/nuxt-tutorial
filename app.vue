<script>
const count = ref(1)
const countUp = () => {
  count++
}
</script>
<template>
  <div>
    <NuxtRouteAnnouncer />
    <p>ああああああああああああああああ</p>
    <p>{{ count }}</p>
    <NuxtWelcome />
  </div>
</template>
