<script>
import AddPlayers from "./components/AddPlayers.vue";
import MyLeaderboard from "./components/MyLeaderboard.vue";
export default {
  components: { AddPlayers, MyLeaderboard },
  data() {
    return {
      players: [],
    };
  },
};
</script>

<template>
  <div id="app">
    <AddPlayers v-model:players="players" />
    <MyLeaderboard v-model:players="players" />
  </div>
</template>
