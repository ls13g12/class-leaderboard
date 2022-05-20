<script>
export default {
  props: ["player"],
  emits: ["update:player"],
};
</script>

<template>
  <tr>
    <td class="name">{{ player.name }}</td>
    <td><button class="decrement" @click="$emit('decrement')">-1</button></td>
    <td>{{ player.score }}</td>
    <td><button class="increment" @click="$emit('increment')">+1</button></td>
    <td class="tiled-img">pictures to be added</td>
  </tr>
</template>
