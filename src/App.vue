<template>
  <div>
    <div class="container">
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow is-offset-1">
          <div class="crop">
            <a href="https://www.progressbar.sk"><img src="./assets/progressbar-logo.svg" alt="progressbar logo">
            </a>
          </div>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a class="button is-warning is-outlined" href="https://donate.progressbar.sk">Send 💶💰⛓ donation</a>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
          <div class="column is-narrow">
            <a @click="enableAutoBlackDoors()" class="button is-white is-outlined">1-click 🚪 </a>
            <a @click="openBlackDoors()" class="button is-white is-outlined">Black 🚪 doors</a>
          </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a @click="turnOffPortal('http://portal1.bar')" class="button is-danger is-outlined">_1_</a>
          <a @click="turnOffPortal('http://portal2.bar')" class="button is-danger is-outlined">_2_</a>
          <a @click="turnOffPortal('http://portal3.bar')" class="button is-danger is-outlined">_3_</a>
          <a @click="turnOffPortal('http://portal4.bar')" class="button is-danger is-outlined">_4_</a>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a @click="turnOnPortal('http://portal1.bar')" class="button is-primary is-outlined">💡 1</a>
          <a @click="turnOnPortal('http://portal2.bar')" class="button is-primary is-outlined">💡 2</a>
          <a @click="turnOnPortal('http://portal3.bar')" class="button is-primary is-outlined">💡 3</a>
          <a @click="turnOnPortal('http://portal4.bar')" class="button is-primary is-outlined">💡 4</a>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a @click="rainbowPortal('http://portal1.bar')" class="button is-primary is-outlined">🌈 1</a>
          <a @click="rainbowPortal('http://portal2.bar')" class="button is-primary is-outlined">🌈 2</a>
          <a @click="rainbowPortal('http://portal3.bar')" class="button is-primary is-outlined">🌈 3</a>
          <a @click="rainbowPortal('http://portal4.bar')" class="button is-primary is-outlined">🌈 4</a>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a @click="rainbowPortalAllOff()" class="button is-danger is-outlined">🏳️‍🌈🌈</a>
        </div>
        <div class="column is-narrow">
          <a @click="rainbowPortalAll()" class="button is-primary is-outlined">🏳️‍🌈🌈</a>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a @click="controlLights('lab', 'right', 'Off')" class="button is-danger is-outlined">🛠 Right</a>
          <a @click="controlLights('lab', 'right', 'On')" class="button is-success is-outlined">🛠 Right</a>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a @click="controlLights('lab', 'left', 'Off')" class="button is-danger is-outlined">🛠 Left</a>
          <a @click="controlLights('lab', 'left', 'On')" class="button is-success is-outlined">🛠 Left</a>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a @click="controlLights('main', 'front', 'Off')" class="button is-danger is-outlined">Deck Front</a>
          <a @click="controlLights('main', 'front', 'On')" class="button is-success is-outlined">Deck Front</a>
        </div>
      </div>
      <div class="columns is-mobile is-centered">
        <div class="column is-narrow">
          <a @click="controlLights('main', 'back', 'Off')" class="button is-danger is-outlined">Deck Back</a>
          <a @click="controlLights('main', 'back', 'On')" class="button is-success is-outlined">Deck Back</a>
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
    },
    controlLights(room, side, toggle) {
      axios({
        method: 'get',
        url: `http://control.bar/lights/${room}/${side}/${toggle}`
      })
      .then(response => {
        console.log(response)
      })
      .catch(e => {
        console.log(e)
      })
    },
    rainbowPortalAll() {
      this.rainbowPortal('http://portal1.bar')
      this.rainbowPortal('http://portal2.bar')
      this.rainbowPortal('http://portal3.bar')
      this.rainbowPortal('http://portal4.bar')
    },
    rainbowPortalAllOff() {
      this.turnOffPortal('http://portal1.bar')
      this.turnOffPortal('http://portal2.bar')
      this.turnOffPortal('http://portal3.bar')
      this.turnOffPortal('http://portal4.bar')
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
    height: 70px;
    overflow: hidden;
    padding: 10px;
}

.crop img {
    /*width: 400px;*/
    height: 200px;
    margin: -128px 0 0 -10px;
}
</style>
