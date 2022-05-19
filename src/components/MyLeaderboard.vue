<script>
import LeaderboardRow from "./LeaderboardRow.vue";
export default {
  components: { LeaderboardRow },
  props: ["players"],
};
</script>

<template>
  <table class="table">
    <tbody>
      <tr>
        <LeaderboardRow
          v-for="(player, index) in players"
          :player="player"
          :index="index"
          :key="player.name"
        />
      </tr>
    </tbody>
  </table>
  <p>
    {{ players }}
  </p>
</template>
