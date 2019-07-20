<template>
  <div class="container">
    <!-- app header to display countdown for the whole game -->
    
    <div class="well">
      <h4>Player</h4>
      <p>{{ player }}</p>
    </div>
    <div class="well">
      <h4>Enemy</h4>
      {{ enemy }}
    </div>
  </div>
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
  display: flex;
  flex-direction: column;
  background-color: #d3d3d3;
  width: 30%;
  margin: 10px auto;
}
</style>


