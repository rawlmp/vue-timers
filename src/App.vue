<template>
  <div id="app">
    <h1>{{timers || ""}} {{timers == 1 ? "Timer":"Timers"}} with Vue Components</h1>
    <hr>
    <p><small>Click the "Add Timer" button to add timers.</small></p>
    <p><small>Every Timer has his own ambit and works by itself.</small></p>
    <p><small>You can Start / Pause / Continue or Stop everyone of them.</small></p>
    <hr>
    <div class="buttons">
      <button class="removeButton" v-if="timers > 0" type="button" name="button" @click="removeTimer">Remove Timer</button>
      <button class="addButton" type="button" name="button" @click="addTimer">Add Timer</button>
      <button class="removeAllButton" v-if="timers > 0" type="button" name="button" @click="timers = 0">Remove All</button>
    </div>
    <div class="timersContainer">
      <div v-if="!timers" class="info">
        <p>Click the button ahead to add Timers!!!</p>
      </div>
      <Timer v-for="timer in timers" :key="timer"/>
    </div>
  </div>
</template>

<script>
import Timer from './components/Timer'
export default {
  name: 'app',
  components: {
    Timer
  },
  data(){
    return{
      timers: null
    }
  },
  methods:{
    addTimer(){
      if(this.timers >=25){
        alert("Maximum of 25 Timers");
        return;
      }
      this.timers++;
    },
    removeTimer(){
      this.timers--;
    }
  }
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.buttons{
  display: flex;
  justify-content: space-around;
  align-items: center;

  width: 60%;
  margin: 60px auto;
}

.timersContainer{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;

  width: 60%;
  margin: 40px auto auto auto;
}

.addButton, .removeButton, .removeAllButton {
    background-color: #4CAF50; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    border-radius: 5px;
}

.removeButton {
    background-color: red;
    color: white;
}

.removeAllButton{
  background-color: blue;
}
</style>
