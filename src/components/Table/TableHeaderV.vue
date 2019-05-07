<template>
  <div class="axs-table-header-v">
    <div v-for="title in cacheTitleListV" :key="title.text" class="axs-table-header-v-item is-center" :style="setStyle(title)">
      <div class="col-wid">{{ title.text }}</div>
      <div v-if="title.children" class="axs-table-header-v-item-rank1-wrapper">
        <div v-for="titleRank1 in title.children" :key="titleRank1.text" class="axs-table-header-v-item-rank1">
          <div class="axs-table-header-v-item-rank1-item">{{ titleRank1.text }}</div>
          <div v-if="titleRank1.children" class="axs-table-header-v-item-rank1-item axs-table-header-v-item-rank2-wrapper">
            <div v-for="titleRank2 in titleRank1.children" :key="titleRank2.text" class="axs-table-header-v-item-rank2">
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
    titleListV: {
      type: Array,
      default: null
    },
    titleHRanks: {
      type: Number,
      default: 3
    }
  },
  data() {
    return {
      cacheTitleListV: []
    }
  },
  watch: {
    titleListV() {
      this.cacheTitleListV = []
      this.setCacheTitleListV()
    }
  },
  mounted() {
    this.setCacheTitleListV()
  },
  methods: {
    setCacheTitleListV() {
      const nullObjList = []
      for (let i = 0; i < this.titleHRanks; i++) {
        if (i === this.titleHRanks - 1) {
          nullObjList.push({
            text: ' '
          })
        } else {
          nullObjList.push({})
        }
      }
      this.cacheTitleListV = this.cacheTitleListV.concat(...nullObjList, ...this.titleListV)
    },
    setStyle(item) {
      const boderStyle = this.setNullBorderStyle(item)
      return {
        ...boderStyle,
        height: this.getHieght(item)
      }
    },
    setNullBorderStyle(item) {
      if (!item.text) {
        return {
          'border-bottom': 0
        }
      }
    },
    getHieght(TitleItem) {
      const HEIGHT = 48
      if (!TitleItem.children) {
        return `${HEIGHT}px`
      }
      let heigths = 0
      TitleItem.children.forEach((item) => {
        if (item.children && item.children.length) {
          item.children.forEach((itemNext) => {
            heigths += HEIGHT
          })
        } else {
          heigths += HEIGHT
        }
      })
      return `${heigths}px`
    }
  }
}
</script>
<style scoped>
.axs-table-header-v {
  border-top: 1px solid #EBEEF5;
  border-left: 1px solid #EBEEF5;
}
.axs-table-header-v-item {
  display: flex;
  min-width: 120px;
  height: 48px;
  line-height: 48px;
  border-right: 1px solid #EBEEF5;
  border-bottom: 1px solid #EBEEF5;
  color: #909399;
  font-weight: 500;
}
.axs-table-header-v-item-rank1:not(:first-child), .axs-table-header-v-item-rank2:not(:first-child) {
  border-top: 1px solid #EBEEF5;
  border-right: 1px solid #EBEEF5;
}
.axs-table-header-v-item-rank1:last-child, .axs-table-header-v-item-rank2:last-child {
  border-right: none;
}
.axs-table-header-v-item-rank1 {
  display: flex;
  min-width: 80px;
}
.axs-table-header-v-item-rank2 {
  flex: 1;
  min-width: 80px;
}
.axs-table-header-v-item-rank-item {
  min-width: 80px;
}
.axs-table-header-v-item-rank1 {
  display: flex;
}
.axs-table-header-v-item-rank1-item {
  min-width: 80px;
  flex: 1;
}
.axs-table-header-v-item-rank1-wrapper, .axs-table-header-v-item-rank2-wrapper {
  flex: 1;
  border-left: 1px solid #EBEEF5;
}
.col-wid {
  width: 80px;
}
.is-center {
  text-align: center;
}
</style>
