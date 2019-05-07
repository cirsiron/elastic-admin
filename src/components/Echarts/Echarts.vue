<template>
  <div ref="eachrts" :style="setWidthAndHeight()" />
</template>
<script>
import echarts from 'echarts'

export default {
  name: 'EachrtLine',
  props: {
    width: {
      type: Number || String,
      default: 400
    },
    height: {
      type: Number || String,
      default: 320
    },
    options: {
      type: Object,
      required: true
    }
  },
  mounted() {
    const myChart = echarts.init(this.$refs.eachrts)
    myChart.setOption({
      ...this.options
    })
  },
  methods: {
    setWidthAndHeight() {
      return {
        width: `${this.width}px`,
        height: `${this.height}px`
      }
    }
  }
}
</script>
