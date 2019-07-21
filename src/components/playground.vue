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
            <div>Life-bar: {{ player }}</div>
          </div>
        </v-card-title>

        <v-card-actions>
          <v-btn flat color="orange">Attack</v-btn>
          <v-spacer></v-spacer>
          <v-btn flat color="orange">Heal</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
    
    <v-flex xs6 sm6 flexbox>
      <v-card>
        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">Enemy</h3>
            <div>Life-bar: {{ enemy }}</div>
          </div>
        </v-card-title>

        <v-card-actions>
          <v-btn flat color="orange">Attack</v-btn>
          <v-spacer></v-spacer>
          <v-btn flat color="orange">Heal</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  name: "playground",
  data: function() {
    return {
      title: "playground resources",
      // add player life equal to 10 life points
      player: 10,
      // add enemy life to 1qual the player life
      enemy: 10
    };
  },
  attackPlayer: function() {
    const deduction = Math.floor(Math.random() * 10);
    return {
      deduction
    };
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


