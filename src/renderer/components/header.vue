<template>
  <header class="toolbar toolbar-header">
      <div class="toolbar-actions">
          <router-link id="logo" to="/">
          <button class="btn btn-default pull-left">
            <span class="icon icon-home"></span>
          </button>
        </router-link>

        <button class="btn btn-default btn-dropdown pull-right" id="modes" @click="switchColorMode">
          {{mode}}
        </button>
      </div>
    </header>
</template>

<script>
export default {
  name: 'hd',
  data () {
    return {
      mode: 'hex'
    }
  },
  methods: {
    switchColorMode () {
      switch (this.mode) {
        case 'hex':
          this.mode = 'rgb'
          break
        case 'rgb':
          this.mode = 'hsl'
          break
        case 'hsl':
          this.mode = 'hex'
          break
      }
      this.$emit('click', this.mode)
    }
  }
}
</script>

<style lang="css">
#top h2{font-size: 1.2rem;}
</style>
