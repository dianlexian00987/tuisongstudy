<template>
  <div class="tab">
    <router-link tag="div" class="tab-item " to="/recommend">
      <span class="tab-link">推荐</span>
    </router-link>
    <router-link tag="div" class="tab-item" to="/singer">
      <span class="tab-link">歌手</span>
    </router-link>
    <router-link tag="div" class="tab-item" to="/rank">
      <span class="tab-link">排行</span>
    </router-link>
    <router-link tag="div" class="tab-item" to="/search">
      <span class="tab-link">搜索</span>
    </router-link>
  </div>
</template>
<script>
export default {
  name: 'tab',
  components: {}
}
</script>

<style scoped lang="stylus">
  @import "~common/stylus/variable"
  .tab
    display flex
    .tab-item
      display flex
      justify-content center
      width 33.3%
      .tab-link
        padding-bottom 5px
        color: $color-text-l
      &.router-link-active
        .tab-link
          color: $color-theme
          border-bottom: 2px solid $color-theme
</style>
