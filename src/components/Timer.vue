<template lang="html">
  <div :class="{ active: working, stopped: counting > 0 && !working, timer: true }">
    <h2>{{counting}}</h2>
    <div v-if="!working" class="buttons">
      <button class="greenButton" type="button" name="button" @click="count">{{counting != 0? "Go":"Start"}}</button>
      <button v-if="counting > 0" type="button" name="button" @click="reset">Reset</button>
    </div>
    <div v-else class="buttons">
      <button class="redButton" type="button" name="button" @click="stop">Pause</button>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      counting: 0,
      working: false,
      interval: null
    };
  },
  methods:{
    count(){
      this.working = true;
      //We need the setInterval function in a variable to stop it later with the clearInterval
      this.interval = setInterval(() => {this.counting++}, 100);
    },
    stop(){
      this.working = false;
      clearInterval(this.interval);
    },
    reset(){
      this.counting = 0;
    }
  }
}
</script>

<style scoped lang="css">
  .timer{
    width: 100px;
    height: 100px;
    border: 1px solid grey;
    border-radius: 5px;
    margin: 10px;
  }

  .active{
    background-color: lightgreen;
    color: white;
  }

  .stopped{
    background-color: lightblue;
    color: white;
  }

  .redButton{
    color: red;
  }

  .greenButton{
    color: green;
  }

  .buttons{
    display: flex;
    justify-content: space-around;
  }
</style>
