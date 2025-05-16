<template>
	<div style="width:580px;height:280px;background:#f5f8fd;border-bottom-right-radius: 20px;"> 
          <div ref="chart"  style="background: #FFFFFF;width:550px;height:260px;margin-right: 20px;margin-left: 10px;    border-top-left-radius: 20px;border-top-right-radius: 20px;border-bottom-right-radius: 20px;text-align:center;line-height: 280px;">
            <!--图表-->
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
	    top: '5%',
	    left: 'center'
	  },
	  graphic: {
	    type: 'text',
	    left: 'center',
	    top: 'center',
	    style: {
	      text: '总访问量\n3147',
	      textAlign: 'center',
	      fill: '#1f78b4',       // 文字颜色
	      fontSize: 14,           // 字体大小
	      fontWeight: 'bold',     // 粗体
	      fontFamily: 'Arial',    // 字体
	      lineHeight: 30,         // 行高
	      textShadowColor: '#999',// 阴影颜色
	      textShadowBlur: 4,      // 阴影模糊
	      textShadowOffsetX: 2,   // 阴影横向偏移
	      textShadowOffsetY: 2    // 阴影纵向偏移
	    }
	  },
	  series: [
	    {
	      name: 'Access From',
	      type: 'pie',
	      radius: ['40%', '70%'],
	      avoidLabelOverlap: false,
	      label: {
	        show: true,                // 开启标签显示
	        position: 'outside',       // 标签位置，显示在外侧
	        formatter: '{b}: {d}%',    // 格式化标签为名称和百分比
	        fontSize: 14,              // 字体大小
	        fontWeight: 'bold'         // 字体粗细
	      },
	      labelLine: {
	        show: true,                // 显示引出线
	        length: 20,                // 引出线的长度
	        length2: 40,               // 第二段引出线的长度
	        lineStyle: {
	          color: '#000',           // 引出线颜色
	          width: 2,                // 引出线宽度
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
	        { value: 1048, name: '一年级' },
	        { value: 735, name: '二年级' },
	        { value: 580, name: '三年级' }
	      ]
	    }
	  ]
	};
	myChart.setOption(option)
	});
</script>