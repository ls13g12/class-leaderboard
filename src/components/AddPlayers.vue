<script>
export default {
  props: ["players"],
  emits: ["update:players"],
  data() {
    return {
      newPlayer: "",
      localPlayers: this.players,
    };
  },
  methods: {
    //user submits name and they are added to list
    submit_name() {
      if (
        this.localPlayers &&
        !this.localPlayers.some((player) => player.name === this.newPlayer)
      ) {
        const newPlayerObject = {
          name: this.newPlayer,
          score: 0,
        };
        this.localPlayers.push(newPlayerObject);
        //sort all players by name
        this.localPlayers.sort((a, b) => (a.name > b.name ? 1 : -1));
        this.$emit("update:players", this.localPlayers);
        this.newPlayer = "";
      }
    },
  },
};
</script>

<template>
  <tr>
    <input id="player-input" v-model="newPlayer" />
    <button type="button" @click="submit_name()">Submit</button>
  </tr>
</template>
