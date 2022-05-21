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
      return topPlayers.map((player) => player.name);
    },
  },
};
</script>

<template>
  <div class="banner">
    <h1 v-if="localPlayers.length < 1">
      Add some players!
    </h1>
    <h1 v-else-if="topScore < 1">
      Nobody has any points yet!
    </h1>
    <h1 v-else-if="topPlayers && topPlayers.length >= 5">
      There are too many winners to choose from!
    </h1>
    <h1 v-else>
      Leading with a score of {{ topScore }} - {{ topPlayers.join(", ") }}
    </h1>
  </div>
</template>

<style>
.banner {
  text-align: center;
}
</style>
