<template>
  <div class="main" style="background-color: chartreuse;">
    <div id="startOfCountdown" v-if="showStartOfCountdown" class="countdown">Time until: {{parsedStartOfCountdown}}</div>
    <TimerPage class="timerPage" :countDownDate="startOfCountdown"/>
  </div>
</template>

<script>
import TimerPage from './components/TimerPage.vue'
export default {
  name: 'App',
  components: {
    TimerPage
  },
  data() {
    return {
      startOfCountdown: new Date(2023, 9, 31, 21, 6),
      showStartOfCountdown: false,
    }
  },
  computed: {
    parsedStartOfCountdown() {
      let year, month, day, hour, minute, second;

      year = this.startOfCountdown.getFullYear();
      month = this.startOfCountdown.getMonth();
      day = this.startOfCountdown.getDay();
      hour = this.startOfCountdown.getHours();
      minute = this.startOfCountdown.getMinutes();
      second = this.startOfCountdown.getSeconds();

      let parsed = `${year} year, ${month} month, ${day} day, ${hour} hour, ${minute} minute, ${second} second`

      return parsed;
    }
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

* {
  margin: 0;
  padding: 0;
}

.main {
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.countdown {
  padding-bottom: 3vh;
}

#startOfCountdown {
  font-size: 3vw;
}

</style>
