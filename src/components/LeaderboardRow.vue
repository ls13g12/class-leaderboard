<script>
export default {
  props: ["player"],
  emits: ["update:player"],
  data() {
    return {
      temp_player: this.player,
    };
  },
  methods: {
    handleIncrementScore() {
      this.temp_player.score += 1;
      this.$emit("update:player");
    },
  },
};
</script>

<template>
  <th>{{ player.name }}</th>
  <th>{{ player.score }}</th>
  <th><button @click="handleIncrementScore()">+1</button></th>
</template>
