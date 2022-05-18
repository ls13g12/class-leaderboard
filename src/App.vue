<script>
import AddPlayers from "./components/AddPlayers.vue";
export default {
  components: { AddPlayers },
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
    <ul>
      <li v-for="player in players" :key="player.name">
        {{ player.name }} with a score of {{ player.score }}
      </li>
    </ul>
  </div>
</template>
