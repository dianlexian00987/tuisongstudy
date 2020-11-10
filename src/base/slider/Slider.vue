<template>
  <div class="slider" ref="slider">
      <div class="slider-group" ref="sliderGroup">
        <slot>
        </slot>
      </div>
      <div class="dots"></div>
  </div>
</template>

<script>
import {addClass} from 'common/js/dom'
import BScroll from 'better-scroll'
export default {
  name: 'Slider',
  props: {
    loop: {
      type: Boolean,
      default: true
    },
    autoPlay: {
      type: Boolean,
      default: true
    },
    interval: {
      type: Number,
      default: 4000
    }
  },
  mounted () {
    setTimeout(() => {
      // 获取图片的宽度
      this.getImageWhiths()
      // 初始化batter-scroll
      this.initBatterScroll()
    }, 20)
  },
  methods: {
    getImageWhiths () {
      this.children = this.$refs.sliderGroup.children
      let width = 0
      let sliderWidth = this.$refs.slider.clientWidth
      console.log(this.children.length)
      console.log(this.children)
      for (let i = 0; i < this.children.length; i++) {
        addClass(this.children[i], 'slider-item')
        this.children[i].style.width = sliderWidth + 'px'
        width += sliderWidth
      }
      this.$refs.sliderGroup.style.width = width + 'px'
      console.log('qqqq', width)
    },
    initBatterScroll () {
      this.slider = new BScroll(this.$refs.slider, {
        scrollX: true,
        scrollY: false,
        momentum: false
      })
    }
  }
}
</script>

<style scoped lang="stylus">
  .slider
    position absolute
    left 0
    top  0
    width 100%
    height 100%
    .slider-group
      position: relative
      overflow: hidden
      white-space: nowrap
      .slider-item
        float: left
        box-sizing: border-box
        overflow: hidden
        .img
          display block
          width 100%
</style>
