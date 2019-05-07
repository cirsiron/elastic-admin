<template>
  <div class="axs-table-body">
    <div v-for="( item, index ) in list" :key="index" class="axs-table-body-outer is-cneter">
      <div v-for="( itemInner, indexInner ) in item" :key="indexInner" class="axs-table-body-inner">
        {{ itemInner }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TableBody',
  props: [],
  data() {
    return {
      list: [
        [11, 12, 13, 14, 15, 16, 17, 18],
        [21, 22, 23, 24, 25, 26, 27, 28],
        [31, 32, 33, 34, 35, 36, 37, 38],
        [41, 42, 43, 44, 45, 46, 47, 48],
        [51, 52, 53, 54, 55, 56, 57, 58],
        [61, 62, 63, 64, 65, 66, 67, 68]
      ]
    }
  }
}
</script>

<style scoped>
.axs-table-body {
  position: relative;
  top: -3px;
  left: 1px;
  min-width: 960px;
  z-index: -1;
}
.axs-table-body-outer {
  display: flex;
  height: 48px;
  line-height: 48px;
}
.axs-table-body-inner {
  min-width: 120px;
  padding: 0 8px;
  border-right: 1px solid #EBEEF5;
  border-bottom: 1px solid #EBEEF5;
}
.is-cneter {
  text-align: center;
}
</style>
