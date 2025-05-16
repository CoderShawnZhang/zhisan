<template>
	<div style="width:580px;height:280px;background:#f5f8fd;border-bottom-right-radius: 20px;"> 
          <div style="background: #FFFFFF;margin-right: 20px;margin-left: 10px;
          border-top-left-radius: 20px ;border-top-right-radius: 20px;border-bottom-right-radius: 20px;
          display:flex;flex-direction:column;height:260px;">
            <span style="margin-top:18px;margin-left:22px;color:#333333;font-size:20px;font-weight: 800;">受众年级占比</span>
           	<div ref="chart"  style="width:550px;height:260px;"><!--图表--></div>
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
	     	orient: 'vertical', // 设置图例垂直排列（可选）
			  left: '3%',       // 设置靠左
			  bottom: '20%',       // 设置在底部 5% 位置
			  textStyle: {
			    fontSize: 12
			 }
	  },
	  graphic: [
	  	 {
		    type: 'text',
		    left: '50%',
		    top: '35%',
		    style: {
		      text: '2.8W',
		      textAlign: 'center',
		      fill: '#4A5BDE',
		      fontSize: 28,
		      fontWeight: '400',
		      fontFamily: 'Arial'
		    }
		  },
		  {
		    type: 'text',
		    left: '50%',
		    top: '50%',
		    style: {
		      text: '出售数量/台',
		      textAlign: 'center',
		      fill: '#999999',
		      fontSize: 12,
		      fontWeight: 'normal',
		      fontFamily: 'Arial'
		    }
		  }
	  ],
	  series: [
	    {
	      name: 'Access From',
	      type: 'pie',
	      radius: ['50%', '70%'], // 增大饼图大小（内半径，外半径）
    	  center: ['56%', '45%'], // 控制图的位置（X%, Y%）
	      avoidLabelOverlap: false,
	      label: {
	        show: true,                // 开启标签显示
	        position: 'outside',       // 标签位置，显示在外侧
	        formatter: function(params) {
            	// 使用 Math.round 四舍五入取整
            	return `${params.name}:${Math.round(params.percent),1}%`
          	},
	        fontSize: 14,              // 字体大小
	        fontWeight: 'bold'         // 字体粗细
	      },
	      labelLine: {
	        show: true,                // 显示引出线
	        length: 20,                // 引出线的长度
	        length2: 40,               // 第二段引出线的长度
	        lineStyle: {
	          width: 1,                // 引出线宽度
	          type: 'solid'            // 引出线类型
	        }
	      },
	      emphasis: {
	        label: {
	          show: true,
	          fontSize: 12,
	        }
	      },
	      data: [
	        { value: 1048, name: '1~2年级', itemStyle: {
    color: {
      type: 'linear',
      x: 0,
      y: 0,
      x2: 1,
      y2: 1,
      colorStops: [
        { offset: 0, color: '#63B9FF' },  // 较浅蓝
    { offset: 1, color: '#1D4FD9' }   // 深蓝
      ]
    }
  }},
	        { value: 735, name: '3~4年级', itemStyle: {
    color: {
      type: 'linear',
      x: 0,
      y: 0,
      x2: 1,
      y2: 1,
      colorStops: [
          { offset: 0, color: '#8ff0cc' },  // 稍深蓝
    { offset: 1, color: '#22ac79' }   // 稍浅蓝
      ]
    }
  } },
	        { value: 580, name: '5~6年级', itemStyle: {
    color: {
      type: 'linear',
      x: 0,
      y: 0,
      x2: 1,
      y2: 1,
      colorStops: [
        { offset: 0, color: '#FFE48D' },  // 浅黄
    { offset: 1, color: '#FBB632' }   // 橙黄
      ]
    }
  } }
	      ]
	    }
	  ]
	};
	myChart.setOption(option)
	});
</script>