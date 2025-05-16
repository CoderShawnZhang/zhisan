<template>
  <div class="contain">
    <div style="color:#333333;font-size:20px;">
      用户做题科目占比
    </div>
    <div>
      <div ref="chart" style="width:100%;height:206px;margin-left: -10px;display: flex;justify-content: center;">
        <!--图表-->
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
  
import * as echarts from 'echarts'


const chart = ref(null)

onMounted(() => {
  const myChart = echarts.init(chart.value)
  
  const option = {
  tooltip: {
    trigger: 'item',
    formatter: '{b}: {c} ({d}%)' // 显示百分比
  },
  legend: {
    show:false
  },
  color: ['#7A89FF', '#00FFC3', '#FF8B8B'], // 颜色数组
  series: [
    {
      name: 'Access From',
      type: 'pie',
      radius: ['50%', '70%'],
      avoidLabelOverlap: false,
      label: {
        show: true,                // 开启标签显示
        position: 'outside',       // 标签位置，显示在外侧
         formatter: function(params) {
            // 使用 Math.round 四舍五入取整
            return `${params.name}:${Math.round(params.percent)}%`
          },
        fontSize: 11,              // 字体大小
        fontWeight: 'bold'         // 字体粗细
      },
      labelLine: {
        show: true,                // 显示引出线
        length: 5,                 // 引出线的长度
        length2: 10,               // 第二段引出线的长度
        lineStyle: {
          width: 1,                // 引出线宽度
          type: 'solid'            // 引出线类型
        }
      },
      emphasis: {
        label: {
          show: true,
          fontSize: 16,
          fontWeight: 'bold'
        }
      },
      data: [
        { value: 1048, name: '语文' },
        { value: 735, name: '数学' },
        { value: 580, name: '英语' }
      ]
    }
  ]
};
myChart.setOption(option)




})
</script>

<style lang="scss" scoped>

</style>
