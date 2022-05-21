<script>
export default {
  props: ["player"],
  emits: ["update:player", "increment", "decrement"],
};
</script>

<template>
  <tr>
    <td class="name">{{ player.name }}</td>
    <td>
      <button 
        class="decrement" 
        @mousedown="$emit('decrement')" 
      >
        -1
      </button>
    </td>
    <td>{{ player.score }}</td>
    <td>
      <button
        class="increment"
        @mousedown="$emit('increment')"
      >
        +1
      </button>
    </td>
    <td class="tiled-img-td">
      <div class="tiled-img-div">
        <img
          class="tiled-img"
          v-for="(n, index) in player.score"
          :key="index"
          src="../assets/maoam-raspberry.png"
        />
      </div>
    </td>
  </tr>
</template>
