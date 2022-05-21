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
    submitName() {
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
    <td class="name">
      <input
        id="player-input"
        v-model="newPlayer"
        v-on:keyup.enter="submitName()"
        placeholder="new name..."
      />
    </td>
  </tr>
</template>
