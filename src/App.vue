<template>
  <div id="app">
    <h1 class="app-title"> Attack & Defend </h1>
    
    <div class="progress-bar">{{ countDownBar }}</div>
    
    <Playground />
    <!-- <Button variant="contained" color="primary">
      Hello World
    </Button>-->
  </div>
</template>

<script>
import Playground from './components/playground';
// import Button from '@material-ui/core/Button';

export default {
  name: "app",
  components: {
    Playground
  },
  data: function(){
    return {
      // implement countdown with js
      countDownBar: ' 3 min countdown to be implemented'
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  align-items: center;
  vertical-align: center;
}
.app-title { 
  padding: 10px;
  font-size: 1.8em;
  font-weight: 400;
}
.progress-bar {
  padding: 10px;
  font-size: 1.3em;
}
</style>
