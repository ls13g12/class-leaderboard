<script>
import MyLeaderboard from "./components/MyLeaderboard.vue";
export default {
  components: { MyLeaderboard },
  data() {
    return {
      players: [],
    };
  },
};
</script>

<template>
  <div id="app">
    <MyLeaderboard v-model:players="players" />
  </div>
</template>
