<template>
  <div id="color" ref="color" class="color pane" :style={backgroundColor:color}>
    <h1 class="color_code">{{color}}</h1>
  </div>
</template>

<script>
import * as Utils from '../../utils/utils'
export default {
  name: 'color',
  props: {
    mode: String
  },
  data () {
    return {
      color: this.colorConvert(this.mode, this.colorGen()),
      hex: this.colorGen(),
      open: false
    }
  },
  watch: {
    mode (value) {
      this.color = this.colorConvert(value, this.hex)
    }
  },
  methods: {
    colorGen () {
      return '#' + Math.random().toString(16).slice(2, 8)
    },
    colorConvert (mode, color) {
      var rgb = Utils.hex2rgb(color)
      var hsl = Utils.rgb2hsl(rgb)
      switch (mode) {
        case 'rgb':
          return `rgb(${rgb.join(', ')})`
        case 'hsl':
          return `hsl(${hsl[0]}, ${hsl[1]}%, ${hsl[2]}%)`
        default:
          return color
      }
    }
  },
  mounted: function () {
    var self = this
    this.$refs.color.onclick = function (e) {
      e.preventDefault()
      if (e.target.tagName === 'H1') {
        Utils.copy(e.target.innerText)
        Utils.toast()
        return
      }
      self.hex = self.colorGen()
      self.color = self.colorConvert(self.mode, self.hex)
    }
  }
}
</script>

<style>
.color{width: 100%;height: 100%;}
body{
  font-size: 1.5em;
  line-height: 1.6;
  font-weight: 400;
  font-family: "Quicksand", "Raleway", "HelveticaNeue", "Helvetica Neue", Helvetica, Arial, sans-serif;
  }
h1.color_code,._404_txt{
  font-size: 2.0rem;
  font-family: "Quicksand";
  font-weight: 300;
  margin: 0 0 2.0rem 0;
  user-select:none;
  cursor: pointer;
  position: fixed;
  color: #fff;
  top: 50%;
  /*
  left: 50%;
  transform: translate(-50%, -50%);
  */
  text-align: center;
  width: 100%;
}
</style>
