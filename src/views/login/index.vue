<template>
  <div class="page-center">
    <div class="login-wrapper">
      <!-- 左侧图片区域 -->
      <div class="login-left">
        <div style="display: flex;flex-direction: column;font-weight: 800;font-size: 12px;color: #FFFFFF;margin:28px auto auto 22px;">
          <span>广东智三信息技术有限公司</span>
          <span style="font-size:24px;">后台管理系统</span>
        </div>
        <div style="width:100%;display:flex;flex-direction:row;justify-content: center;align-items: center;">
          <div style="width:296px;height:296px;">
          <el-image
            :src="loginBanner"
            fit="cover"
            style="width: 100%; height: 100%"
          />
          </div>
        </div>
      </div>
      <!-- 右侧登录区域 -->
      <div class="login-right">
        <div class="login-title">账号登录</div>
        <div class="login-box" style="height:295px;">
          <transition name="fade-slide" mode="out-in">
            <component
              :is="formComponents[component]"
              v-model="component"
              class="w-full"
            />
          </transition>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import logo from "@/assets/logo.png";
import defaultSettings from "@/settings";
import loginBanner from "@/assets/images/login_left@2x.png";

type LayoutMap = "login";

const t = useI18n().t;

const component = ref<LayoutMap>("login");
const formComponents = {
  login: defineAsyncComponent(() => import("./components/Login.vue")),
};
</script>

<style lang="scss" scoped>
.page-center {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;     /* 垂直居中 */
  justify-content: center; /* 水平居中 */
  
   background: url("@/assets/images/login-gb.png");
    background-size: cover;
}

.login-wrapper {
  width: 800px;
  height: 400px;
  display: flex;
  background-color: #fff;
  border-radius: 10px;
  overflow: hidden;
}

.login-left {
  width: 50%;
  height: 100%;
  background: linear-gradient( 224deg, #5064FF 0%, #91B8FF 100%);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
}

.login-right {
  width: 50%;
  padding: 18px 20px;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.login-box {
  width: 344px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 20px;
}

.login-title {
  font-size: 24px;
  text-align: center;
  color: #666666;
  height:105px;
  width: 100%;
  text-align: right;
}
</style>
