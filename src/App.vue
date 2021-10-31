<template>
  <div id="app">
    <div :class="{'higher-font-size': increaseFontSize}">{{timerValue}}</div>
    <button v-on:click="startTimer">Start timer</button>
    <button v-on:click="stopTimer">Stop timer</button>
    <button v-on:click="resetTimer">Reset timer</button>
    <button v-on:click="increaseFontsize">Increase Font Size</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: () => {
    return {
      timerValue: 0,
      timerId: null,
      increaseFontSize: false,
    }
  },
  components: {},
  methods:{
    startTimer() {
      this.timerId = setInterval(()=>{
        this.timerValue++;
      }, 1000);
    },
    stopTimer() {
      clearInterval(this.timerId);
    },
    resetTimer() {
      clearInterval(this.timerId);
      this.timerValue = 0;
    },
    increaseFontsize() {
      this.increaseFontSize = true;
    },
  },
}
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.higher-font-size {
  font-size: 24px;
}
</style>
