<template>
  <div class="axs-table">
    <Eachrts :options="options" />
    <TableContent :title-list="titleList" />
  </div>
</template>
<script>
import { TableContent } from '@/components/Table'
import { Eachrts } from '@/components/Echarts'
export default {
  name: 'AxsTable',
  components: {
    TableContent,
    Eachrts
  },
  data() {
    return {
      titleList: {
        h: [
          {
            text: 'title1',
            isCenter: true,
            children: [
              {
                text: 'title1-1',
                isCenter: true,
                children: [
                  {
                    text: 'title1-1-1',
                    isCenter: true
                  },
                  {
                    text: 'title1-1-2',
                    isCenter: true
                  }
                ]
              }, {
                text: 'title1-2',
                isCenter: true
              }
            ]
          }, {
            text: 'title2',
            children: [
              {
                text: 'title2-1',
                isCenter: true,
                children: [
                  {
                    text: 'title2-1-1',
                    isCenter: true
                  },
                  {
                    text: 'title2-1-2',
                    isCenter: true
                  }
                ]
              }, {
                text: 'title2-2',
                isCenter: true
              }
            ]
          }, {
            text: 'title3'
          }, {
            text: 'title4'
          }
        ],
        v: [
          {
            text: 'title1',
            isCenter: true,
            children: [
              {
                text: 'title1-2',
                isCenter: true
              }
            ]
          }, {
            text: 'title2',
            children: [
              {
                text: 'title2-1',
                isCenter: true,
                children: [
                  {
                    text: 'title2-1-1',
                    isCenter: true
                  },
                  {
                    text: 'title2-1-2',
                    isCenter: true
                  }
                ]
              }, {
                text: 'title2-2',
                isCenter: true
              }
            ]
          }, {
            text: 'title3'
          }, {
            text: 'title4'
          }
        ]
      },
      options: {
        xAxis: {
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
          type: 'value'
        },
        series: [{
          data: [820, 932, 901, 934, 1290, 1330, 1320],
          type: 'line'
        }]
      }
    }
  }
}
</script>
<style scoped>
</style>
