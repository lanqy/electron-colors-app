<template>
  <div id="app" class="window">
    <Hd @click="switchColorMode"></Hd>
    <div class="window-content">
      <div class="pane-group">
      <Side @click="handlerClick"></Side>
      <router-view :route="route" :mode="mode"></router-view>
    </div>
    </div>
  </div>
</template>

<script>
import './assets/css/photon.min.css'
import Hd from './components/header.vue'
import Side from './components/sidebar.vue'
export default {
  name: 'app',
  data () {
    return {
      route: 'red',
      open: false,
      mode: 'hex'
    }
  },
  methods: {
    handlerClick (key) {
      this.route = key
    },
    close () {
      var _this = this
      setTimeout(function () {
        _this.open = false
      }, 1000)
    },
    switchColorMode (value) {
      this.mode = value
    }
  },
  components: {
    Side,
    Hd
  }
}
</script>

<style>
*{margin:0;padding:0;}
html,body{height: 100%;width:100%}
#color,#side{height:100%;overflow:auto;display: flex;-ms-flex-direction:column;flex-direction:column;overflow-x:hidden;padding:4px 4px 0;-webkit-overflow-scrolling:touch;will-change:transform}
#color li,#side a{width:100%;display:block;border-radius:4px;margin-bottom:4px}
#side{padding: 0 4px 0;}
#side a{width: 100%;
    display: block;
    border-radius: 4px;
    margin-bottom: 4px;
    min-height: 4rem;
    line-height: 4rem;
    color: #fff;
}
#color li{position: relative;min-height: 5em;}
#color label,#color span{position:absolute;font-weight:700;font-size:80%}
#color label{top:.5em;left:.5em}
#color span{font-style:italic;right:.5em;bottom:.5em}

#toast {
    position: fixed;
    background-color: #fff;
    box-shadow: 0 1px 3px rgba(33, 33, 33, 0.12), 0 1px 2px rgba(33, 33, 33, 0.24);
    transition: -webkit-transform .3s cubic-bezier(0.4, 0, 0.2, 1) 0.2s;
    transition: transform .3s cubic-bezier(0.4, 0, 0.2, 1) 0.2s;
    transition: transform .3s cubic-bezier(0.4, 0, 0.2, 1) 0.2s,
    -webkit-transform .3s cubic-bezier(0.4, 0, 0.2, 1) 0.2s;
    will-change: transform;
    border-radius: 2px;
    padding: 0.75em 1.5em;
    font-weight: 700;
    top: -2em;
    left: 50%;
    -webkit-transform: translateX(-50%);
    transform: translateX(-50%);
    z-index: 1;
}
#toast.open {
    -webkit-transform: translate(-50%, 4.375em);
    transform: translate(-50%, 4.375em)
}
#app {
  font-family: 'Quicksand', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 100%;
  width: 100%;
  color: #2c3e50;
}
._404{
  -webkit-flex: 1;
    -ms-flex: 1;
    flex: 1;
    width: 100%;
    background: #666;
  }
</style>
