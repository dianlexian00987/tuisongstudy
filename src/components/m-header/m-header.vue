<template>
   <div class="m-header">
      <div class="photo">
        <img src="./logo@2x.png" alt="" class="img">
        <h4 class="name">Chicken Music</h4>
      </div>
      <div class="user">
        <i class="icon-mine"></i>
      </div>
   </div>

</template>

<script>
export default {
  name: 'm-header'
}
</script>

<style scoped lang="stylus">
  @import "~common/stylus/variable"
  .m-header
    display flex
    width 100%
    height 44px
    line-height 44px
    .photo
      display flex
      width 100%
      justify-content center
      .img
        display inline-block
        vertical-align center
        width 26px
        height 26px
        margin-top 7px
        margin-right 4px
      .name
        color $color-theme
    .user
      margin-right 6px
      color $color-theme
</style>
