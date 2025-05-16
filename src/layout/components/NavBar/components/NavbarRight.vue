<template>
  <div :class="['navbar__right', navbarRightClass]">
    <!-- 桌面端显示 -->
    <template v-if="isDesktop">
      <!-- 搜索
      <MenuSearch />
       -->
      <!-- 全屏
      <Fullscreen />
       -->
      <!-- 布局大小
      <SizeSelect />
       -->
      <!-- 语言选择
      <LangSelect />
       -->
      <!-- 通知下拉
      <NoticeDropdown />
      -->
    </template>

    <!-- 用户头像（个人中心、注销登录等） -->
    <div style="margin-right:72px;">
      <el-popover
        placement="bottom-end"
        :width="256"
        :height="125"
        :show-arrow="false"
        popper-class="custom-popover"
      >
         <template #default>
          <div style="height:125px;display: flex;flex-direction: column;justify-content: space-between;">
              <div style="display:flex;margin-left:8px;align-items: center;margin-top:17px;">
                <div style="width: 44px; height: 44px; border-radius: 50%; overflow: hidden;margin-right:16px;">
                  <img
                    src="https://img01.sogoucdn.com/v2/thumb/retype_exclude_gif/ext/auto/q/80/crop/xy/ai/t/0/w/562/h/752?appid=122&url=https://img02.sogoucdn.com/app/a/100520020/928e6b29b3366e23b846471fd8ef16fe"
                    style="width: 100%; height: 100%; object-fit: cover;" />
                </div>
               
                <div style="display:flex;flex-direction:column">
                  <span style="color:#333333;font-size:20px;font-weight:400;">曹阿满</span>
                  <span style="color:#333333;font-size:14px;font-weight:400;">账号：32559915</span>
                </div>
              </div>
              <div style="font-size:16px;display: flex;width: 100%;justify-content: space-around;">
                <span style="color:#FD6466;">退出登录</span>
                <div style="width:0;height:16px;border: 1px solid #999999;"></div>
                <span>切换账号</span>
              </div>
          </div>
        </template>

        <template #reference>
          <div class="user-profile">
            <img class="user-profile__avatar" :src="userStore.userInfo.avatar" style="margin-right:15px;"/>
            <span class="user-profile__name">{{ userStore.userInfo.username }}</span>
            <el-icon><CaretBottom /></el-icon>
          </div>
        </template>
      </el-popover>
    </div>
    <!-- 设置面板 -->
    <div v-if="defaultSettings.showSettings" @click="settingStore.settingsVisible = true">
      <div class="i-svg:setting" />
    </div>
  </div>
</template>
<script setup lang="ts">
const { t } = useI18n();
import defaultSettings from "@/settings";
import { DeviceEnum } from "@/enums/settings/device.enum";
import { useAppStore, useSettingsStore, useUserStore, useTagsViewStore } from "@/store";

import { SidebarColor, ThemeMode } from "@/enums/settings/theme.enum";


const appStore = useAppStore();
const settingStore = useSettingsStore();
const userStore = useUserStore();
const tagsViewStore = useTagsViewStore();

const route = useRoute();
const router = useRouter();
const isDesktop = computed(() => appStore.device === DeviceEnum.DESKTOP);

/**
 * 打开个人中心页面
 */
function handleProfileClick() {
  router.push({ name: "Profile" });
}

// 根据主题和侧边栏配色方案选择 navbar 右侧的样式类
const navbarRightClass = computed(() => {
  // 如果暗黑主题
  if (settingStore.theme === ThemeMode.DARK) {
    return "navbar__right--white";
  }

  // 如果侧边栏是经典蓝
  if (settingStore.sidebarColorScheme === SidebarColor.CLASSIC_BLUE) {
    return "navbar__right--white";
  }
});

/**
 * 注销登录
 */
function logout() {
  ElMessageBox.confirm("确定注销并退出系统吗？", "提示", {
    confirmButtonText: "确定",
    cancelButtonText: "取消",
    type: "warning",
    lockScroll: false,
  }).then(() => {
    userStore
      .logout()
      .then(() => {
        tagsViewStore.delAllViews();
      })
      .then(() => {
        router.push(`/login?redirect=${route.fullPath}`);
      });
  });
}
</script>

<style lang="scss" scoped>
.navbar__right {
  display: flex;
  align-items: center;
  justify-content: center;

  & > * {
    display: flex;
    align-items: center;
    justify-content: center;
    min-width: 40px;
    height: $navbar-height;
    color: var(--el-text-color);
    text-align: center;
    cursor: pointer;

    &:hover {
      background: rgb(0 0 0 / 10%);
    }
  }
  .user-profile {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    padding: 0 13px;

    &__avatar {
      width: 32px;
      height: 32px;
      border-radius: 50%;
    }

    &__name {
      margin-left: 10px;
    }
  }
}

.layout-top .navbar__right--white > *,
.layout-mix .navbar__right--white > * {
  color: #fff;

  // 强制所有svg图标为白色（包括通知图标）
  :deep(svg) {
    color: #fff;
    fill: #fff;
  }
}

.dark .navbar__right > *:hover {
  color: #ccc;
}

/* 如果是全局 style，直接这样写 */
.custom-popover {
  border-radius: 20px !important;
  overflow: hidden !important;
}

/* 如果你的 style 是 scoped，需要这样写： */
:deep(.custom-popover) {
  border-radius: 20px !important;
  overflow: hidden !important;
}
</style>
