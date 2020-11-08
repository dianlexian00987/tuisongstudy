<template>
  <div id="app">
      <mheader></mheader>
      <tab></tab>
    <!--router 的点击-->
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
  </div>
</template>

<script type="text/ecmascript-6">
import mheader from 'components/m-header/m-header'
import tab from 'components/tab/tab'
export default {
  name: 'App',
  components: {
    mheader,
    tab
  }
}
</script>

<style scoped lang="stylus">
</style>
