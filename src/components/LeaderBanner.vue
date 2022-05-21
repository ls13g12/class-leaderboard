<script>
export default {
  props: ["players"],
  data() {
    return {
      localPlayers: this.players,
    };
  },
  computed: {
    topScore() {
      return Math.max(...this.localPlayers.map((player) => player.score));
    },
    topPlayers() {
      const topPlayers = this.localPlayers.filter(
        (player) => player.score === this.topScore
      );
      return topPlayers.map((player) => player.name).join(", ");
    },
  },
};
</script>

<template>
  <div class="banner">
    <h2 v-if="localPlayers.length > 0">
      Leading with a score of {{ topScore }} - {{ topPlayers }}
    </h2>
    <h2 v-else>Add some players!</h2>
  </div>
</template>

<style>
.banner {
  text-align: center;
}
</style>
