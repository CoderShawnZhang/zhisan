<template>
	  <div style="position: relative;background:#fff;height:40px;width:503px;border:1px solid #6E7CE5;border-radius:30px;padding: 0 10px;display: flex;align-items: center;">
        <el-input v-model="input" class="custom-input" />
        <div class="searchBtn">搜索</div>
        <div style="height:40px;width:40px;background:#4A5BDE;border-radius:50px;position: absolute;right: -60px;    display: flex;justify-content: center;align-items: center;">
          <el-image :src="searchMore" style="width:22px;height:21px;cursor: pointer;"/>
        </div>
      </div>
</template>

<script lang="ts" setup>
	import searchMore from "@/assets/images/searchMore@2x.png";
</script>
<style lang="scss" scoped>
  .custom-input ::v-deep(.el-input__wrapper) {
    height: 40px;
    border-radius: 30px;
    padding: 0 15px;
    background-color: transparent;
    box-shadow: none;
    border: none;
  }

  .custom-input ::v-deep(.el-input__inner) {
    height: 40px;
    line-height: 40px;
    border: none;
  }

  .searchBtn{
    width: 80px;
    height: 40px;
    background: #4A5BDE;
    border-radius: 20px;
    color: #fff;
    text-align: center;
    line-height: 40px;
    margin-right: -10px;
    cursor: pointer;
  }


</style>