<style>
@import '../assets/table.css';
</style>

<script>
import LeaderboardRow from "./LeaderboardRow.vue";
export default {
  components: { LeaderboardRow },
  props: ["players"],
};
</script>

<template>
  <table class="table">
    <LeaderboardRow
      v-for="(player, index) in players"
      :player="player"
      :index="index"
      :key="player.name"
      @increment="() => (player.score += 1)"
      @decrement="() => (player.score > 0 ? (player.score -= 1) : pass)"
    />
  </table>
</template>
