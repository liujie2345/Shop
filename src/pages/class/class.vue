<template>
  <div>
    <div class="left">
      <class-left></class-left>
    </div>
    <div class="right">
      <class-right></class-right>
    </div>
  </div>
</template>

<script>
import classLeft from './components/left'
import classRight from './components/right'
export default {
  components: {
    classLeft,
    classRight
  }
}
</script>

<style lang="stylus">
.left
  position fixed
  top 0
  left 0
  bottom 0
  width 25%
.right
  position absolute
  top 0
  right 0
  width 75%
</style>

