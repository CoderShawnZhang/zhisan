<template>
	<div style="height:230px;margin:20px;margin-top:0;background: #FFFFFF;">
    <div ref="chart" style="width: 100%; height: 100%;"></div>
  </div>
</template>

<script setup lang="ts">
	import * as echarts from 'echarts'
	const chart = ref(null)
	onMounted(() => {
	  const myChart = echarts.init(chart.value)
	  const option = {
	    xAxis: {
	      type: 'category',
	      data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun','Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
	    },
	    yAxis: {
	      type: 'value'
	    },
	    series: [
	      {
	        data: [120, 200, 150, 80, 70, 110, 130,120, 200, 150, 80, 70, 110, 130],
	        type: 'bar'
	      }
	    ]
	  };
	  myChart.setOption(option)
	});
</script>