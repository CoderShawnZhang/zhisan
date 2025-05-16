<template>
  <div class="dashboard-container">
      <CountModule/>
      <div class="bottomRegional">
        <BingChart/> 
        <Regional/>
      </div>
      <ZhuChart/>
  </div>
</template>

<script setup lang="ts">
//引入组件
import BingChart from "./components/bingChart.vue";
import ZhuChart from "./components/zhuChart.vue";
import Regional from "./components/regional.vue";
import CountModule from "./components/countModule.vue";

//引入样式
import './style/css.scss'
</script>

