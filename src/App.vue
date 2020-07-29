<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="start-receiving" @click="startReceiving">START_RECIEVING</div>
    <div class="topic" @click="topic(`TOPIC`)">TOPIC</div>
    <div class="stop-receiving" @click="stopReceiving">STOP_RECIEVING</div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    startReceiving() {
      window.webkit.messageHandlers.FcmStartRecieving.postMessage(`START_RECIEVING`);
    },
    topic(topic) {
      window.webkit.messageHandlers.FcmRegisterTopic.postMessage(`${topic}`);
    },
    stopReceiving() {
      window.webkit.messageHandlers.FcmStopReceiving.postMessage(`STOP_RECIEVING`);
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
  margin-top: 60px;
}

.start-receiving {
  width: 200px;
  background-color: red;
  color: white;
  padding: 8px;
  margin: 0 auto 20px;
}

.topic {
  width: 200px;
  border: 1px solid black;
  color: black;
  padding: 8px;
  margin: 0 auto 20px;
}

.stop-receiving {
  width: 200px;
  background-color: blue;
  color: white;
  padding: 8px;
  margin: 0 auto 20px;
}
</style>
