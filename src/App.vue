<template>
<div id="app">
      <header>
            <span>HQ.bar - WiP</span>
      </header>
      <main>
            <button @click="turnOnPortal('http://portal.bar')">Turn On Portal</button></br>
            <button @click="turnOnPortal('http://portal2.bar')">Turn On Portal 2</button></br>
            <button @click="turnOffPortal('http://portal.bar')">Turn off Portal</button></br>
            <button @click="turnOffPortal('http://portal2.bar')">Turn off Portal 2</button></br>
            <button @click="hackerPortal('http://portal2.bar')">hacker Portal 2</button></br>
            <!-- <router-view></router-view> -->
      </main>
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'app',
  methods: {
    turnOffPortal(target) {
      axios({
          method: 'post',
          baseURL: target,
          params: {
            r: 1023,
            g: 1023,
            b: 1023
          }
        })
        .then(response => {
          console.log(response);
        })
        .catch(e => {
          console.log(e);
        })
    },
    turnOnPortal(target) {
      axios({
          method: 'post',
          baseURL: target,
          params: {
            r: 1,
            g: 1,
            b: 1
          }
        })
        .then(response => {
          console.log(response);
        })
        .catch(e => {
          console.log(e);
        })
    },
    hackerPortal(target) {
      axios({
          method: 'post',
          baseURL: target,
          params: {
            r: 1023,
            g: 23,
            b: 990
          }
        })
        .then(response => {
          console.log(response);
        })
        .catch(e => {
          console.log(e);
        })
    }

  }
}
</script>

<style>
body {
    margin: 0;
}

#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: x§§ grayscale;
    color: #2c3e50;
}

main {
    text-align: center;
    margin-top: 40px;
}

header {
    margin: 0;
    height: 56px;
    padding: 0 16px 0 24px;
    background-color: #35495E;
    color: #ffffff;
}

header span {
    display: block;
    position: relative;
    font-size: 20px;
    line-height: 1;
    letter-spacing: .02em;
    font-weight: 400;
    box-sizing: border-box;
    padding-top: 16px;
}
</style>
