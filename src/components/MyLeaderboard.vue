<style>
@import "../assets/base.css";
</style>

<script>
import LeaderboardRow from "./LeaderboardRow.vue";
import AddPlayers from "./AddPlayers.vue";
export default {
  components: { LeaderboardRow, AddPlayers },
  props: ["players"],
  emits: ["update:players"],
  data() {
    return {
      incrementInterval: null,
      decrementInterval: null,
      localPlayers: this.players,
    };
  },
  methods: {
    increment(name) {
      this.incrementBy1(name);
      this.incrementInterval = setInterval(() => {
        this.incrementBy1(name);
      }, 100);
    },
    incrementBy1(name) {
      //selected player object for unique player in players
      this.localPlayers.filter((player) => player.name == name)[0].score += 1;
    },
    decrement(name) {
      this.decrementBy1(name);
      this.decrementInterval = setInterval(() => {
        this.decrementBy1(name);
      }, 100);
    },
    decrementBy1(name) {
      //selected player object for unique player in players
      const selectedPlayer = this.localPlayers.filter(
        (player) => player.name == name
      )[0];
      if (selectedPlayer.score > 0) {
        selectedPlayer.score -= 1;
      }
      //this.localPlayers[name] += 1;
    },
    mouseup() {
      clearInterval(this.incrementInterval);
      clearInterval(this.decrementInterval);
      this.$emit("update:players", this.localPlayers);
    },
  },
};
</script>

<template>
  <!-- stop continous continous counting with mouseup anywhere on table-->
  <table class="table" @mouseup="mouseup">
    <LeaderboardRow
      v-for="(player, index) in localPlayers"
      :player="player"
      :index="index"
      :key="player.name"
      @increment="increment(player.name)"
      @decrement="decrement(player.name)"
    />
    <AddPlayers :players="players" />
  </table>
</template>
