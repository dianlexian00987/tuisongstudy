<template>
  <div class="recommend" v-if="swipper.length">
    <div class="recommend-header-content">
      <Slider>
        <div class="imgs" v-for="(item ,index) in swipper" :key="index"  >
          <img class="img" :src="item.picUrl" alt="" @load="imageLoad">
        </div>
      </Slider>
    </div>
    <div class="class-body-content">
      <h3 class="hot-music-title">热门歌曲推荐</h3>
      <ul class="hot-music-list">
        <li class="hot-music-item" v-for="(item,index) in musicList" :key="index">
          <div class="hot-img">
            <img :src="item.imgurl" alt="" class="img">
          </div>
          <div class="hot-content">
            <h4 class="title" v-text="item.creator.name"></h4>
            <p class="content" v-text="item.dissname"></p>
          </div>
        </li>
      </ul>
    </div>

  </div>

</template>

<script>
import {getRecommend, getDiscList} from 'api/Recommend'
import {ERR_OK} from 'api/config'
import Slider from 'base/slider/Slider'
export default {
  name: 'Recommend',
  components: {
    Slider
  },
  created () {
    this._getRecommend()
    // 获取列表的数据
    this._getSongList()
  },
  data () {
    return {
      swipper: [],
      musicList: []
    }
  },
  methods: {
    _getRecommend: function () {
      getRecommend().then((res) => {
        if (res.code === ERR_OK) {
          this.swipper = res.data.slider
          // console.log(this.swipper)
        }
      })
    },

    _getSongList () {
      getDiscList().then((res) => {
        if (res.code === ERR_OK) {
          console.log(res)
          this.musicList = res.data.list
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
    left 0
    right 0
    top 80px
    bottom 0
    overflow hidden
    position fixed
    .imgs
      width 100%
      height 100%
    .class-body-content
      overflow hidden
      padding 10px
      .hot-music-title
        height 80px
        line-height 80px
        text-align center
        color #ffcd32
      .hot-music-list
        width 100%
        .hot-music-item
          display flex
          margin-bottom 10px
         .hot-img
            width 80px
            height 80px
            .img
              width 100%
              height 100%
         .hot-content
            flex 1
            margin-left 16px
            .title
              height 30px
              line-height 30px
              margin-bottom 10px
            .content
              color blanchedalmond
</style>
