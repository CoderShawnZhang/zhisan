<template>
  <div class="LeftLtL">
    <div style="color:#333333;font-size:20px;">
      用户测评记录
    </div>
    <div class="scroll-wrap" style="font-size:14px;color:#666666;display:flex;flex-direction:column;    height: 100px;overflow-y: auto;    line-height: 25px;">
      <div>
        <span style="color:#4A5BDE;">《期末测试》</span>
        <span style="font-weight: 100;">2025年06月12日 16：30~18：30</span>
      </div>
      <div>
        <span style="color:#4A5BDE;">《期末测试》</span>
        <span style="font-weight: 100;">2025年06月12日 16：30~18：30</span>
      </div>
      <div>
        <span style="color:#4A5BDE;">《期末测试》</span>
        <span style="font-weight: 100;">2025年06月12日 16：30~18：30</span>
      </div>
      <div>
        <span style="color:#4A5BDE;">《期末测试》</span>
        <span style="font-weight: 100;">2025年06月12日 16：30~18：30</span>
      </div>
      <div>
        <span style="color:#4A5BDE;">《期末测试》</span>
        <span style="font-weight: 100;">2025年06月12日 16：30~18：30</span>
      </div>
      <div>
        <span style="color:#4A5BDE;">《期末测试》</span>
        <span style="font-weight: 100;">2025年06月12日 16：30~18：30</span>
      </div>
    </div>
    <!--遮罩-->
    <div class="gradient-mask"></div>
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
  .LeftLtL{
    position: relative;
  }
   /* 滚动条样式 */
  .scroll-wrap::-webkit-scrollbar {
    width: 2px;
  }

  .scroll-wrap::-webkit-scrollbar-thumb {
    background-color: rgba(110, 124, 229, 0.6);
    border-radius: 4px;
  }

  .scroll-wrap::-webkit-scrollbar-track {
    background-color: transparent;
  }

  /* 底部渐变遮罩 */
  .gradient-mask {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 50px;
    background: linear-gradient(to bottom, rgba(255,255,255,0), rgba(255,255,255,1));
    pointer-events: none; /* 不遮挡点击和滚动 */
  }
</style>
