<template>
  <div v-if="isShow" class="lazy-loader">
    <slot></slot>
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
