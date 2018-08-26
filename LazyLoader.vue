<template>
  <div class="lazy-loader">
    <!-- v-if只能放到第二级 -->
    <slot v-if="isShow"></slot>
  </div>
</template>

<script>
export default {
  data () {
    return {
      io: null,
      isShow: ''
    }
  },
  mounted () {
    this.io = new IntersectionObserver(entries => {
      if (entries[0].isIntersecting) {
        this.isShow = true
      }
    })
    this.io.observe(this.$el)
  },
  beforeDestroy () {
    // 关闭观察器
    this.io.disconnect()
  }
}
</script>

<style scoped>
  .lazy-loader {
    height: 100%;
    width: 100%;
  }
</style>
