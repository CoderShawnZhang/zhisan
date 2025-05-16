<template>
  <div class="contain">
    <span>权限管理</span>
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
  .contain{
    font-size:12;
    color:#999999;
    display: flex;
    flex-direction: column;
    width: 100%;
    justify-content: center;
    align-items: center;
    margin-bottom:39px;
  }
</style>
