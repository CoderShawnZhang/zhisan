<template>
  <div class="navbar">
    <div class="navbar__left">
      <!-- 展开/收缩菜单
      <Hamburger :is-active="isSidebarOpened" @toggle-click="toggleSideBar" />
        -->
      <!-- 面包屑 
      <Breadcrumb />
      -->
      <div style="width: 100%;display: flex;justify-content: space-between;">
        <div style="display: flex;align-items: center;margin-left:45px;">
          <el-image :src="noticeImg" style="height:28px;width:28px;"/>
          <span style="font-size:16px;color:#666666;margin-left:12px;">曹阿瞒，早上好啊，您有一个待办哦~</span>
        </div>
        <div style="margin-right:51px;color:#999999;font-size:20px;">2025年06月01日 9：20</div>
      </div>
    </div>
    <!-- 导航栏右侧 -->
    <NavbarRight />
  </div>
</template>

<script setup lang="ts">
import { useAppStore } from "@/store";
import noticeImg from "@/assets/images/notice@2x.png";
const appStore = useAppStore();

// 侧边栏是否打开
const isSidebarOpened = computed(() => appStore.sidebar.opened);

// 展开/收缩菜单
function toggleSideBar() {
  appStore.toggleSidebar();
}
</script>

<style lang="scss" scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  height: $navbar-height;
  background: var(--el-bg-color);
  border-bottom: 1px solid #f5f8fd;
  &__left {
    display: flex;
    align-items: center;
    width: 100%;
  }
}
</style>
