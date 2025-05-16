<template>
  <div>
    <span>安全管理</span>
    <SelectProvince/>
  </div>
</template>

<script lang="ts" setup>

import SelectProvince from "@/components/SelectProvince/index.vue"
defineProps({
  collapse: {
    type: Boolean,
    required: true,
  },
});
</script>

<style lang="scss" scoped>

</style>
