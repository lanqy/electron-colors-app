<template>
    <div class="pane pane-sm sidebar">
      <nav class="nav-group" id="side">
        <h5 class="nav-group-title">Colors</h5>
        <router-link v-for="key in keys" :to="'/material/'+key" :style="'text-align:left;text-decoration:none;background-color:'+ colors[key].base.hex">
          <span class="nav-group-item" @click="handlerClick(key)">
            <span :style="'color:'+ colors[key].base.hex"></span>
            {{key}}
          </span>
        </router-link>
      </nav>
    </div>
</template>

<script>
import json from '../../utils/colors/colors.json'
export default {
  name: 'sidebar',
  data () {
    return {
      colors: json,
      keys: Object.keys(json)
    }
  },
  methods: {
    handlerClick (key) {
      this.$emit('click', key)
    }
  }
}
</script>
<style>
</style>
