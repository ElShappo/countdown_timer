<template>
  <div class="main">
    <div class="countdown">Countdown starts from: {{countDown}}</div>
    <TimerPage class="timerPage" :countDownDate="countDown"/>
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
      countDown: new Date(2024, 5, 4, 20, 24),
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

</style>
