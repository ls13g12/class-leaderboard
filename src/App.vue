<script>
import MyLeaderboard from "./components/MyLeaderboard.vue";
import LeaderBanner from "./components/LeaderBanner.vue";
export default {
  components: { MyLeaderboard, LeaderBanner },
  data() {
    return {
      players: [],
    };
  },
};
</script>

<template>
  <div id="app">
    <LeaderBanner v-model:players="players" />
    <MyLeaderboard v-model:players="players" />
  </div>
</template>
