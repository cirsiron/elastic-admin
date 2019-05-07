<template>
  <div class="axs-table-content clearfix">
    <TableHeaderV :title-list-v="titleListV" />
    <TableHeaderH v-if="direction === 'horizontal'" :title-list="titleListH" :direction="direction" />
    <TableBody />
  </div>
</template>

<script>
import TableHeaderH from './TableHeaderH'
import TableHeaderV from './TableHeaderV'
import TableBody from './TableBody'

export default {
  name: 'TableHeader',
  components: {
    TableHeaderH,
    TableHeaderV,
    TableBody
  },
  props: {
    direction: {
      type: String,
      default: 'horizontal'
    },
    titleList: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      titleListV: this.titleList.v || [],
      titleListH: this.titleList.h || []
    }
  }
}
</script>

<style scoped>
.axs-table-content {
  min-width: 1216px;
}
.axs-table-content >>> .axs-table-header-v {
  float: left;
}
</style>
