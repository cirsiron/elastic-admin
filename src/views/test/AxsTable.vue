<template>
  <div class="axs-table">
    <TableContent :title-list="titleList" />
  </div>
</template>
<script>
import { TableContent } from '@/components/Table'

export default {
  name: 'AxsTable',
  components: {
    TableContent
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
      }
    }
  }
}
</script>
<style scoped>
</style>
