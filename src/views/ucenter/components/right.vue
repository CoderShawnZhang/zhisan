<template>
  <div class="contain">
    <div style="color:#333333;font-size:20px;font-weight:800;">
      功能使用占比/小时
    </div>
    <!--统计进度-->
    <div style="display:flex;flex-direction:column;margin-top:24px;">
        <div v-for="(item,index) in usageList" style="display:flex;align-items: center;" :style="{ marginTop: index !== 0 ? '11px' : '0' }">
          <span class="processText">{{item.label}}</span>
          <div class="processLine" :style="{ width: item.value + '%' }"></div>
        </div>
    </div>
    <!--统计数量-->
    <div style="width:131px;height:26px;display:flex;border:1px solid #4A5BDE;border-radius:4px;align-items: center;margin-top:13px;">
      <span style="color:#999999;font-size:12px;margin:4px 5px;">其他</span>
      <span style="color:#4A5BDE;margin-left:12px;font-weight: 800;font-size: 20px;">5559</span>
    </div>
    
    <div style="display:flex;justify-content: space-between;margin-top:9px;">
      <div style="width:60px;height:52px;border-radius: 4px;border: 1px solid #4A5BDE;display: flex;flex-direction: column;align-items: center;">
        <span style="font-size:20px;color:#4A5BDE;font-weight: 800;">5559</span>
       <span style="font-size:12px;color:#999999">AI自习</span>
      </div>
      <div style="width:60px;height:52px;border-radius: 4px;border: 1px solid #4A5BDE;display: flex;flex-direction: column;align-items: center;">
        <span style="font-size:20px;color:#4A5BDE;font-weight: 800;">593</span>
       <span style="font-size:12px;color:#999999">AI批改</span>
      </div>
      <div style="width:60px;height:52px;border-radius: 4px;border: 1px solid #4A5BDE;display: flex;flex-direction: column;align-items: center;">
        <span style="font-size:20px;color:#4A5BDE;font-weight: 800;">659</span>
       <span style="font-size:12px;color:#999999">AI测评</span>
      </div>
      <div style="width:60px;height:52px;border-radius: 4px;border: 1px solid #4A5BDE;display: flex;flex-direction: column;align-items: center;">
        <span style="font-size:20px;color:#4A5BDE;font-weight: 800;">24</span>
       <span style="font-size:12px;color:#999999">AI分析</span>
      </div>
      <div style="width:60px;height:52px;border-radius: 4px;border: 1px solid #4A5BDE;display: flex;flex-direction: column;align-items: center;">
        <span style="font-size:20px;color:#4A5BDE;font-weight: 800;">12</span>
       <span style="font-size:12px;color:#999999">AI报告</span>
      </div>
      <div style="width:60px;height:52px;border-radius: 4px;border: 1px solid #4A5BDE;display: flex;flex-direction: column;align-items: center;">
        <span style="font-size:20px;color:#4A5BDE;font-weight: 800;">55595559</span>
        <span style="font-size:12px;color:#999999">我的世界</span>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
  const usageList = [
    { label: 'AI自习', value: 13 },
    { label: 'AI批改', value: 48 },
    { label: 'AI测评', value: 80 },
    { label: 'AI分析', value: 27 },
    { label: 'AI报告', value: 65 },
    { label: '我的世界', value: 52 },
    { label: '其他', value: 39 },
  ]
</script>

<style lang="scss" scoped>
  .contain{
    width: 100%;
    display:flex;
    flex-direction:column;
  }

  .processText{
    text-align: right;
    color: #666666;
    font-size: 16px;
    width: 80px;
    padding-right: 10px;
  }

  .processLine{
    width:100%;
    height:10px;
    background: linear-gradient( 90deg, #A3FFE9 0%, #4A5BDE 100%);
    border-radius: 4px 4px 4px 4px;
  }
</style>
