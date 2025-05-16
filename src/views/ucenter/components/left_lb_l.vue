<template>
  <div class="LeftLbL">
    <div style="color:#333333;font-size:20px;">
      用户使用信息
    </div>
    <div style="display: flex;flex-direction: column;font-size:16px;font-weight: 100;">
      <div style="margin-top:12px;">
        <span style="color: #333333;font-weight: 400;">使用时长</span>
        <span style="color: #666666;">：90天16小时32分钟</span>
      </div>
      <div style="margin-top:12px;">
        <span style="color: #333333;font-weight: 400;">做题数量</span>
        <span style="color: #666666;">：326492/道 正确率：85％</span>
      </div>
      <div style="margin-top:12px;">
        <span style="color: #333333;font-weight: 400;">数学</span>
        <span style="color: #666666;">：126492/道 正确率：35.2％</span>
      </div>
      <div style="margin-top:12px;">
        <span style="color: #333333;font-weight: 400;">语文</span>
        <span style="color: #666666;">：126492/道 正确率：30.2％</span>
      </div>
      <div style="margin-top:12px;">
        <span style="color: #333333;font-weight: 400;">英语</span>
        <span style="color: #666666;">：126492/道 正确率：34.6％</span>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
defineProps({
  collapse: {
    type: Boolean,
    required: true,
  },
});
</script>

<style lang="scss" scoped>
  .LeftLbL{

  }
</style>
