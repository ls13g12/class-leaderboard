<style scoped src="../assets/table.css"></style>

<script>
export default {
  props: ["player"],
  emits: ["update:player"],
};
</script>

<template>
  <tr>
    <th>{{ player.name }}</th>
    <th><button class="decrement" @click="$emit('decrement')">-1</button></th>
    <th>{{ player.score }}</th>
    <th><button class="increment" @click="$emit('increment')">+1</button></th>
  </tr>
</template>
