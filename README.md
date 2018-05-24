# LazyLoader

安装
```
npm i -save lazy-loader-puge
或
yarn add lazy-loader-puge
```

## 使用

```
<template lang="pug">
  .panel-item
    LazyLoader.lazy(:url="'./static/assets/thumbnails/' + chartData.id + '.png'")
      img(:src="'./static/assets/thumbnails/' + chartData.id + '.png'")
</template>

<script>
import LazyLoader from 'lazy-loader-puge'
export default {
  components: {
    LazyLoader
  }
}
</script>

<style lang='less' scoped>
  .lazy {
    width: 200px;
    height: 200px;
  }
</style>

```