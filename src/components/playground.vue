<template>
  <!-- implement vuetify layout :done -->
  <!-- implement life reduction and healing abilities -->
  <!-- implement special weapons to aid the user -->
  <!-- implement battle sound and ambience for the app -->
  <!-- research functions for cool effects -->
  <!-- represent both player and enemy avators -->
  <!-- use animations to show attacks and healing happenning in app -->
  <v-layout row nowrap>
    <v-layout row style="width: 100%;">
        <v-flex xs6 v-if="playerLost" style="margin-top: 20px; margin-left: auto; margin-right: auto;">
          <v-card >
          <v-card-title>
            <h6 v-text="finalMessage" style="color: red; text-align: center; font-weight: 200; font-size: 1.3em;">{{finalMessage}}</h6>
            <v-btn color="green" flat href="/">Restart Game?</v-btn>
          </v-card-title>
        </v-card>
        </v-flex>
        <v-flex xs6 v-else-if="playerWon" style="margin-top: 20px; margin-left: auto; margin-right: auto;">
          <v-card >
          <v-card-title>
            <h6 v-text="finalMessage" style="color: red; text-align: center; font-weight: 200; font-size: 1.3em;">{{finalMessage}}</h6>
            <v-btn color="green" flat href="/">Restart Game?</v-btn>
          </v-card-title>
        </v-card>
        </v-flex>

      <v-flex xs6 flexbox v-if="!playerLost">
        <v-card>
          <v-card-title primary-title>
            <div>
              <h3 class="headline mb-0">Player</h3>
              <span>Life: {{ this.showPlayerLife() }}</span>
            </div>
          </v-card-title>
          
          <v-card-actions v-if="!playerWon">
            <v-btn flat color="red" @click="this.attackBoss" >Attack</v-btn>
            <v-btn flat color="orange" @click="this.defendPlayer" >Defend</v-btn>
            <!-- <v-spacer></v-spacer> -->
            <v-btn flat color="green" @click="this.healPlayer">Heal</v-btn>
          </v-card-actions>
        </v-card>
        
      </v-flex>
      
      

      <v-flex xs6 sm6 flexbox v-if="!enemyLost">
        <v-card>
          <v-card-title primary-title>
              <div>
                <h3 class="headline mb-0">Boss</h3>
              <span>Life: {{ enemy }}</span>
              </div>
          </v-card-title>
          <v-card-text>
            <span >Enemy still strong enough to fight</span>
            
          </v-card-text>
        </v-card>      
      </v-flex>
    </v-layout>
    
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
      playerWon: false,
      enemyLost: false,
      finalMessage: ''
    };
  },
  methods: {
    showPlayerLife: function(){
      let life = this.player;
      this.playerLifeCheck(life);
      // console.log(life);
      return life;
    },
    attackBoss : function() {
    const deduction = Math.floor(Math.random() * 20);
    if(this.enemy > 0) {
      // console.log(deduction);
      this.enemy = this.enemy - deduction;
      this.enemyLifeCheck(this.enemy);
      // console.log(this.enemy);  
    } else {
      this.enemy = 0;
    }
    // boss also attacks player similtaneously
    const damage = Math.floor(Math.random() * 10);
    if (this.player > 0 && this.player <=100){
      this.player = this.player - damage;
      return this.player;
      // console.log(this.player);
    } else {
      this.player = 0;
    }

    // return deduction;
    },
    defendPlayer: function(){
      const damage = Math.floor(Math.random() * 3);
      if (this.player > 0 && this.player <=100){
        this.player = this.player - damage;
        return this.player;
        // console.log(this.player);
      } else {
        this.player = 0;
      }
    },
    healPlayer: function(){
      if(this.player >= 1 && this.player <= 99){
        let healingPoints = Math.floor(Math.round(Math.random()* 13));
        // console.log(healingPoints);
        this.player = this.player + healingPoints;
        if (this.player > 100){
          // console.log(this.player);
          this.player = 100;
          return this.limitLife(this.player);
        }
        return this.player;
      }
      const damage = Math.floor(Math.random() * 5);
      if (this.player > 0 && this.player <=100){
        this.player = this.player - damage;
        return this.player;
        // console.log(this.player);
      } else {
        this.player = 0;
      }
    },
    limitLife: function (life) {
      setInterval(() => {
        let checkLifeState = life;
        // console.log(checkLifeState);
        if(checkLifeState > 100){
            let maxValue = 100;
            checkLifeState = maxValue;
            // console.log(checkLifeState);
            return checkLifeState;
        } else if(checkLifeState < 0){
          let minValue = 0;
          checkLifeState = minValue;
          return minValue;
        }
      }, 100);
    },
    playerLifeCheck: function(playerLife){
        let currentPlayerLife = playerLife;
        if(currentPlayerLife <= 0) {
          this.playerLost = true;
          // just for playing with different displays
          this.playerWon = false;
          let lostMsg = 'You lost... Try again.';
          this.finalMessage = lostMsg;
          // console.log(this.finalMessage);
          return this.finalMessage;
        } else if (playerLife > 100) {
          let highestLife = 100;
          playerLife = highestLife;
          return playerLife;
        }
    },
    enemyLifeCheck: function (enemyLife){
      let currentPlayerLife = enemyLife;
        if(currentPlayerLife <= 0) {
          this.enemyLost = true;
          this.playerWon = true;
          // console.log(this.enemyLost);
          let lastMsg = 'You Won... Start A new game?';
          this.finalMessage = lastMsg;
          this.playerWon = true;
          // console.log(this.finalMessage);
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


