<template>
  <div class="recommend">
    div.
  </div>

</template>

<script>
import {getRecommend} from 'api/Recommend'
export default {
  name: 'Recommend',
  created () {
    this._getRecommend()
  },
  methods: {
    _getRecommend () {
      getRecommend().then((res) => {
        console.log(res)
      })
    }
  }
}
</script>

<style scoped>

</style>
