<template>
  <div>
    <div class="container">
      <div class="columns is-mobile">
        <div class="column">
          <div class="crop">
            <a href="https://www.progressbar.sk"><img src="./assets/progressbar-logo.svg" alt="progressbar logo">
            </a>
          </div>
        </div>
      </div>
      <div class="columns is-mobile">
        <div class="column is-narrow is-offset-1">
          <a href="https://donate.progressbar.sk"><button class="button is-warning is-outlined">Send 💶💰⛓ donation</button></a>
        </div>
      </div>
      <div class="columns is-mobile">
        <div class="column is-narrow is-offset-1">
          <button @click="turnOffPortal('http://portal.bar')" class="button is-danger is-outlined">Off 0</button>
        </div>
        <div class="column is-narrow">
          <button @click="turnOffPortal('http://portal4.bar')" class="button is-danger is-outlined">Off 4</button>
        </div>
        <div class="column is-narrow">
          <button @click="turnOffPortal('http://portal3.bar')" class="button is-danger is-outlined">Off 3</button>
        </div>
      </div>
      <div class="columns is-mobile">
        <div class="column is-narrow is-offset-1">
          <button @click="rainbowPortal('http://portal.bar')" class="button is-primary is-outlined">🌈 0</button>
        </div>
        <div class="column is-narrow">
          <button @click="rainbowPortal('http://portal4.bar')" class="button is-primary is-outlined">🌈 4</button>
        </div>
        <div class="column is-narrow">
          <button @click="rainbowPortal('http://portal3.bar')" class="button is-primary is-outlined">🌈 3</button>
        </div>
      </div>
      <div class="columns is-mobile">
          <div class="column is-narrow is-offset-1">
            <button @click="turnOnPortal('http://portal.bar')" class="button is-primary is-outlined">⚡️💡 Portal</button>
          </div>
          <div class="column is-narrow">
            <button @click="turnOnPortal('http://portal4.bar')" class="button is-primary is-outlined">⚡️💡 Portal 4</button>
          </div>
      </div>

      <div class="columns is-mobile">
          <div class="column is-narrow is-offset-1">
            <button @click="enableAutoBlackDoors()" class="button is-white is-outlined">1-click 🚪 </button>
          </div>
          <div class="column is-narrow">
            <button @click="openBlackDoors()" class="button is-white is-outlined">Open Black 🚪 </button>
          </div>
      </div>
    </div>
  </div>
  <!-- <router-view></router-view> -->
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'app',
  data() {
    return {
      bitcoinPrice: 1
    }
  },
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
    rainbowPortal(target) {
      var colors = {
        r: Math.floor((Math.random() * 1023) + 1),
        g: Math.floor((Math.random() * 1023) + 1),
        b: Math.floor((Math.random() * 1023) + 1)
      }
      axios({
        method: 'post',
        baseURL: target,
        params: colors
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
    },
    enableAutoBlackDoors() {
      axios({
        method: 'get',
        url: 'http://door.bar/enableauto',
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
    background-color: #000;
}

.crop {
    /*width: 200px;*/
    height: 150px;
    overflow: hidden;
    padding: 10px;
}

.crop img {
    /*width: 400px;*/
    /*height: 300px;*/
    margin: -128px 0 0 -10px;
}
</style>
