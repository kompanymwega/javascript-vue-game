<template>
  <!-- implement vuetify layout :done -->
  <!-- implement life reduction and healing abilities -->
  <!-- implement special weapons to aid the user -->
  <!-- implement battle sound and ambience for the app -->
  <!-- research functions for cool effects -->
  <!-- represent both player and enemy avators -->
  <!-- use animations to show attacks and healing happenning in app -->
  <v-layout row wrap>
    <v-flex xs6 flexbox>
      <v-card>
        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">Player</h3>
            <div>Life: {{ player }}</div>
          </div>
        </v-card-title>

        <v-card-actions>
          <v-btn flat color="red" >Attack</v-btn>
          <v-spacer></v-spacer>
          <v-btn flat color="green">Heal</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>

    <v-flex xs6 sm6 flexbox>
      <v-card>
        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">Boss Level 1</h3>
            <div>Life: {{ enemy }}</div>
          </div>
        </v-card-title>
        <v-card-text>
          <span>stats about enemy</span>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  name: "playground",
  data() {
    return {
      title: "playground resources",
      // add player life equal to 10 life points
      player: 100,
      // add enemy life to 1qual the player life
      enemy: 200
    };
  },
  attackPlayer : () => {
    const deduction = Math.floor(Math.random() * 10);

    return deduction;
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  background: linear-gradient(to top, #ff6bb5de 2%, #f86464 100%);
  padding: 20px;
}
.well {
  display: inline-block;
  background-color: #d3d3d3;
  width: 30%;
  margin-left: 10vw;
}
</style>


