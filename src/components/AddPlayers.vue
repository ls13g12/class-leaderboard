<script>
export default {
  emits: ["update:players"],
  data() {
    return {
      players_entered: "",
      temp_players: [],
    };
  },
  methods: {
    //user submits a names into the sidebar, one per line, and they are stored as a sorted list
    submit_names() {
      this.temp_players = [];
      let _players = this.players_entered
        .split("\n")
        .filter((n) => n)
        .sort();
      for (let player of _players) {
        let new_player = { name: player, score: 0 };
        this.temp_players.push(new_player);
      }
      //sort all players by name
      this.temp_players.sort((a, b) => (a.name > b.name ? 1 : -1));
      this.$emit("update:players", this.temp_players);
    },
  },
};
</script>

<template>
  <textarea name="players" v-model="players_entered"></textarea>
  <button type="button" @click="submit_names()">Submit</button>
</template>

<style>
textarea {
  width: 500px;
}
</style>
