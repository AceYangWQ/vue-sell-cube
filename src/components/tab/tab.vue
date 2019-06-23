<template>
  <div class="tab">
    <cube-tab-bar
      :useTransition=false
      :showSlider=true
      v-model="selectedLabel"
      :data="tabs"
      ref="tabBar"
      class="border-bottom-1px"
    >
    </cube-tab-bar>
    <div class="slide-wrapper">
      <cube-slide
        :loop=false
        :auto-play=false
        :show-dots=false
        :initial-index="index"
        ref="slide"
        :options="slideOptions"
      >
        <cube-slide-item>
          <seller></seller>
        </cube-slide-item>

        <cube-slide-item>
          <goods></goods>
        </cube-slide-item>

        <cube-slide-item>
          <ratings></ratings>
        </cube-slide-item>
      </cube-slide>
    </div>
  </div>
</template>

<script>
  import Seller from 'components/seller/seller'
  import Goods from 'components/goods/goods'
  import Ratings from 'components/ratings/ratings'

  export default {
    name: 'tab',
    components: {
      Seller,
      Goods,
      Ratings
    },
    data () {
      return {
        index: 0,
        slideOptions: {
          listenScroll: true,
          probeType: 3,
          directionLockThreshold: 0
        },
        tabs: [{
          label: '商品'
        }, {
          label: '评论'
        }, {
          label: '商家'
        }]
      }
    },
    computed: {
      selectedLabel: {
        get () {
          return this.tabs[this.index].label
        },
        set (newVal) {
          this.index = this.tabs.findIndex((value) => {
            return value.label === newVal
          })
        }
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~common/stylus/variable"

  .tab
    display: flex
    flex-direction: column
    height: 100%

    >>> .cube-tab
      padding: 10px 0
      font-size: 16px

    .slide-wrapper
      flex: 1
      overflow: hidden
</style>
