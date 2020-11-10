<template>
  <div class="recommend" v-if="swipper.length">
    <Slider>
        <div class="imgs" v-for="(item ,index) in swipper" :key="index"  >
          <img class="img" :src="item.picUrl" alt="" @load="imageLoad">
        </div>
    </Slider>
  </div>

</template>

<script>
import {getRecommend} from 'api/Recommend'
import {ERR_OK} from 'api/config'
import Slider from 'base/slider/Slider'
export default {
  name: 'Recommend',
  components: {
    Slider
  },
  created () {
    this._getRecommend()
  },
  data () {
    return {
      swipper: []
    }
  },
  methods: {
    _getRecommend () {
      getRecommend().then((res) => {
        if (res.code === ERR_OK) {
          this.swipper = res.data.slider
        }
      })
    },
    imageLoad () {
      // 更新页面  重新计算滑动高度

    }
  }
}
</script>

<style scoped lang="stylus">
  .recommend
    width 100%
    height 0
    padding-bottom 40%
    overflow hidden
    position relative
</style>
