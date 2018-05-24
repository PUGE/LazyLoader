<template>
  <div class="lazy-loader">
    <slot v-if="isShow"></slot>
  </div>
</template>

<script>
let io = null
export default {
  data () {
    return {
      isShow: ''
    }
  },
  mounted () {
    io = new IntersectionObserver(entries => {
      if (entries[0].isIntersecting) {
        this.isShow = true
      }
    })
    io.observe(this.$el)
  },
  beforeDestroy () {
    // 关闭观察器
    io.disconnect()
  }
}
</script>

<style scoped>
  .lazy-loader {
    height: 100%;
    width: 100%;
  }
</style>
