<template>
  <section class="container hero is-dark">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Mission control
      </h1>
      <h2 class="subtitle">
        Progressbar hackerspace
      </h2>
      <div class="columns is-desktop">
        <div class="column is-offset-1">
          <button @click="turnOffPortal('http://portal.bar')" class="button is-large is-danger is-outlined">Turn Off Portal</button>
        </div>
        <div class="column is-offset-1">
          <button @click="turnOffPortal('http://portal2.bar')" class="button is-large is-danger is-outlined">Turn Off Portal 2</button>
        </div>
        <div class="column is-offset-1">
          <button @click="turnOnPortal('http://portal.bar')" class="button is-large is-primary is-outlined">Turn On Portal</button>
        </div>
        <div class="column is-offset-1">
          <button @click="turnOnPortal('http://portal2.bar')" class="button is-large is-primary is-outlined">Turn On Portal 2</button>
        </div>
        <div class="column is-offset-1">
          <button @click="hackerPortal('http://portal2.bar')" class="button is-large is-success is-outlined">Hacker Portal 2</button>
        </div>
        <div class="column is-offset-1">
          <button @click="openBlackDoors()" class="button is-large is-white is-outlined">Open Black doors</button>
        </div>
      </div>
    </div>
  </div>


      <!-- <router-view></router-view> -->
</section>
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
          console.log(response)
        })
        .catch(e => {
          console.log(e)
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
          console.log(response)
        })
        .catch(e => {
          console.log(e)
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
          console.log(response)
        })
        .catch(e => {
          console.log(e)
        })
    },
    openBlackDoors() {
      axios({
        method: 'get',
        url: 'http://door.bar/outsidedoor',
      })
      .then(response => {
        console.log(response)
      })
      .catch(e => {
        console.log(e)
      })
    }

  }
}
</script>

<style>
@import "~bulma/css/bulma.css";

html {
    background-color: #363636;
}
/*

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
}*/
</style>
