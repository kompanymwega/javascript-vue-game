<template>
  <!-- implement vuetify layout :done -->
  <!-- implement life reduction and healing abilities -->
  <!-- implement special weapons to aid the user -->
  <!-- implement battle sound and ambience for the app -->
  <!-- research functions for cool effects -->
  <!-- represent both player and enemy avators -->
  <!-- use animations to show attacks and healing happenning in app -->
  <v-layout row nowrap>
    <v-flex xs6 flexbox>
      <v-card>
        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">Player</h3>
            <div>Life: {{ player }}</div>
          </div>
        </v-card-title>
        
        <v-card-actions v-if="!playerLost">
          <v-btn flat color="red" @click="this.attackBoss" >Attack</v-btn>
          <v-btn flat color="orange" @click="this.defendPlayer" >Defend</v-btn>
          <v-spacer></v-spacer>
          <v-btn flat color="green" @click="this.healPlayer">Heal</v-btn>
        </v-card-actions>
        <v-card-actions v-else>
          <h3 v-text="finalMessage" color="red">{{finalMessage}}</h3> 
        </v-card-actions>

      </v-card>
      
    </v-flex>
    
    <v-spacer></v-spacer>

    <v-flex xs6 sm6 flexbox>
      <v-card>
        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">Boss Level 1</h3>
            <div>Life: {{ enemy }}</div>
          </div>
        </v-card-title>
        <v-card-text>
          <span v-if="!enemyLost">Enemy still strong enough to fight</span>
          <h6 v-else v-text="finalMessage" color="red">{{finalMessage}}</h6> 
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
      enemy: 200,
      playerLost: false,
      enemyLost: false,
      finalMessage: ''
    };
  },
  methods: {
    attackBoss : function() {
    const deduction = Math.floor(Math.random() * 20);
    if(this.enemy > 0) {
      console.log(deduction);
      this.enemy = this.enemy - deduction;
      this.enemyLifeCheck(this.enemy);
      console.log(this.enemy);  
    } else {
      this.enemy = 0;
    }
    // boss also attacks player similtaneously
    const damage = Math.floor(Math.random() * 10);
    if (this.player > 0){
      this.player = this.player - damage;
      this.playerLifeCheck(this.player);
      console.log(this.player);
    } else {
      this.player = 0;
    }

    // return deduction;
    },
    defendPlayer: function(){},
    healPlayer: function(){},
    playerLifeCheck: function(playerLife){
        let currentPlayerLife = playerLife;
        if(currentPlayerLife <= 0) {
          this.playerLost = true;
          let lostMsg = 'You lost... Try again.';
          this.finalMessage = lostMsg;
          console.log(this.finalMessage);
          return this.finalMessage;
        }
    },
    enemyLifeCheck: function (enemyLife){
      let currentPlayerLife = enemyLife;
        if(currentPlayerLife <= 0) {
          this.enemyLost = true;
          console.log(this.enemyLost);
          let lastMsg = 'You Won... Start A new game?';
          this.finalMessage = lastMsg;
          console.log(this.finalMessage);
          return this.finalMessage;
        }
    }
  },
  computed:{
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


