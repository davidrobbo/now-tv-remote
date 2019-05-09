<template>
  <div id="app">
    <div id="now-remote">
      <div class="row">
        <div class="col-12">
          <div class="float-left">
            <i style="margin: 10px 0 0 10px" class="fa fa-arrow-left" @click="press('Back')"></i>
          </div>
          <div class="float-right">
            <i style="margin: 10px 10px 0 0" class="fa fa-home" @click="press('Back')"></i>
          </div>
        </div>
        <div class="col-12" style="margin: 40px 0;">
          <div class="col-12">
            <i class="fa fa-chevron-up" @click="press('Up')"></i>
          </div>
          <div class="col-12">
            <i class="fa fa-chevron-left" @click="press('Left')"></i>
            <i style="margin:15px;" class="fa fa-check-circle" @click="press('Select')"></i>
            <i class="fa fa-chevron-right" @click="press('Right')"></i>
          </div>
          <div class="col-12">
            <i class="fa fa-chevron-down" @click="press('Down')"></i>
          </div>
        </div>
        <div class="col-4">
          <i class="fa fa-backward" @click="press('Rev')"></i>
        </div>
        <div class="col-4">
          <i class="fa fa-play" @click="press('Play')"></i>
        </div>
        <div class="col-4">
          <i class="fa fa-forward" @click="press('Fwd')"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import config from '@/config'
export default {
  name: 'App',
  data () {
    return {
      keys: {
        13: 'Select', // Enter
        37: 'Left',
        38: 'Up',
        39: 'Right',
        40: 'Down',
        66: 'Back', // b
        70: 'Fwd', // f
        72: 'Home', // h
        80: 'Play', // p
        82: 'Rev' // r
      }
    }
  },
  methods: {
    press (key) {
      axios.post(`${config.TV_IP}keypress/${key}`)
        .then(() => { /* NoOp */ })
        .catch(console.log)
    },
    onKeyDown (e) {
      const keyCode = e.keyCode
      if (this.keys.hasOwnProperty(keyCode)) {
        this.press(this.keys[keyCode])
      }
    }
  },
  beforeDestroy () {
    document.removeEventListener('keydown', this.onKeyDown)
  },
  mounted () {
    document.addEventListener('keydown', this.onKeyDown)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#now-remote {
  background: #949292;
  display: inline-block;
  width: 220px;
  border-radius: 10%;
  position: relative;
  padding: 20px;
}
.fa {
  color: #fff;
  cursor: pointer;
}
</style>
