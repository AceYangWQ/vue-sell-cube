<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab-wrapper">
      <tab></tab>
    </div>
  </div>
</template>

<script>
  import { getSeller } from 'api'
  import VHeader from 'components/v-header/v-header'
  import Tab from 'components/tab/tab'

  export default {
    name: 'app',
    components: {
      VHeader,
      Tab
    },
    data () {
      return {
        seller: {}
      }
    },
    methods: {
      _getSeller() {
        getSeller().then(seller => {
          this.seller = seller
        })
      }
    },
    created () {
      this._getSeller()
    }
  }
</script>
<style lang="stylus">
  #app
    .tab-wrapper
      position: fixed
      top: 136px
      left: 0
      right: 0
      bottom: 0
</style>
