<template>
  <div class="axs-table-header-h clearfix" :style="{height: getHeightStyle()}">
    <div v-for="title in titleList" :key="title.text" class="axs-table-header-item is-center">
      {{ title.text }}
      <div v-if="title.children" class="axs-table-header-h-item-rank1-wrapper">
        <div v-for="titleRank1 in title.children" :key="titleRank1.text" class="axs-table-header-h-item-rank1" :style="{ width: getWidthStyle(titleRank1)}">
          {{ titleRank1.text }}
          <div v-if="titleRank1.children" class="axs-table-header-h-item-rank2-wrapper">
            <div v-for="titleRank2 in titleRank1.children" :key="titleRank2.text" class="axs-table-header-h-item-rank2">
              {{ titleRank2.text }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TableHeaderH',
  props: {
    direction: {
      type: String,
      default: 'horizontal'
    },
    titleList: {
      type: Array,
      required: true
    }
  },
  methods: {
    getWidthStyle(title) {
      const WIDTH = 120
      let lastLen = 1
      if (title && title.children) {
        const lenList = title.children.map((item) => {
          if (item.children) {
            return item.children.length
          } else {
            return 1
          }
        })
        const maxWid = Math.max(lenList)
        const len = title.children.length
        lastLen = maxWid > len ? maxWid : len
      }
      const wid = title.width || WIDTH
      return `${wid * lastLen}px`
    },
    getHeightStyle() {
      const HEIGHT = 48
      let ran2Height = 0
      let ran3Height = 0
      this.titleList.forEach((item) => {
        ran2Height = HEIGHT * 2
        if (item.children) {
          item.children.forEach((itemNext) => {
            if (itemNext.children) {
              ran3Height = HEIGHT * 3
            }
          })
        }
      })
      return `${ran3Height || ran2Height || HEIGHT}px`
    }
  }
}
</script>
<style scoped>
.axs-table-header-h {
  display: inline-block;
  border-top: 1px solid #EBEEF5;
  border-bottom: 1px solid #EBEEF5;
}
.axs-table-header-item {
  float: left;
  height: 100%;
  line-height: 48px;
  color: #909399;
  font-weight: 500;
  min-width: 120px;
  border-right: 1px solid #EBEEF5;
}
.axs-table-header-h-item-rank1-wrapper, .axs-table-header-h-item-rank2-wrapper {
  display: flex;
}
.axs-table-header-h-item-rank1, .axs-table-header-h-item-rank2 {
  border-top: 1px solid #EBEEF5;
  border-right: 1px solid #EBEEF5;
}
.axs-table-header-h-item-rank1:last-child, .axs-table-header-h-item-rank2:last-child {
  border-right: 0;
}
.axs-table-header-h-item-rank1:last-child {
  border-right: none;
}
.axs-table-header-h-item-rank2 {
  flex: 1;
}
.is-center {
  text-align: center;
}
</style>
