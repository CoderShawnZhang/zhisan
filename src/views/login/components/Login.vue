<template>
  <div>
    <el-form ref="loginFormRef" :model="loginFormData" :rules="loginRules" size="large">
      <!-- 用户名 -->
      <el-form-item prop="username">
        <el-input
          v-model.trim="loginFormData.username"
          :placeholder="t('login.username')"
          class="custom-input"
        />
      </el-form-item>

      <!-- 密码 -->
      <el-tooltip :visible="isCapsLock" :content="t('login.capsLock')" placement="right">
        <el-form-item prop="password">
          <el-input
            v-model.trim="loginFormData.password"
            :placeholder="t('login.password')"
            type="password"
            @keyup="checkCapsLock"
            @keyup.enter="handleLoginSubmit"
            class="custom-input"
          />
        </el-form-item>
      </el-tooltip>

      <!-- 登录按钮 -->
      <el-form-item>
        <el-button :loading="loading" style="background:#4A5BDE;color:#FFFFFF;border-radius: 25px;margin-top:22px;height:48px;" class="w-full" @click="handleLoginSubmit">
          {{ t("login.login") }}
        </el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script setup lang="ts">
import type { FormInstance } from "element-plus";
import { LocationQuery, RouteLocationRaw, useRoute } from "vue-router";
import { useI18n } from "vue-i18n";
import AuthAPI, { type LoginFormData } from "@/api/auth.api";
import router from "@/router";
import { useUserStore } from "@/store";

const { t } = useI18n();
const userStore = useUserStore();
const route = useRoute();


const loginFormRef = ref<FormInstance>();
const loading = ref(false);
const isCapsLock = ref(false);
const captchaBase64 = ref();

const loginFormData = ref<LoginFormData>({
  username: "",
  password: "",
  captchaKey: "",
  captchaCode: "",
  rememberMe: false,
});

const loginRules = computed(() => ({
  username: [
    {
      required: true,
      trigger: "blur",
      message: t("login.message.username.required"),
    },
  ],
  password: [
    {
      required: true,
      trigger: "blur",
      message: t("login.message.password.required"),
    },
    {
      min: 6,
      message: t("login.message.password.min"),
      trigger: "blur",
    },
  ]
}));


async function handleLoginSubmit() {
  try {
    const valid = await loginFormRef.value?.validate();
    if (!valid) return;
    loading.value = true;

    await userStore.login(loginFormData.value);
    await userStore.getUserInfo();

    const redirect = resolveRedirectTarget(route.query);
    await router.push(redirect);
  } catch (error) {
    console.error("登录失败:", error);
  } finally {
    loading.value = false;
  }
}

function resolveRedirectTarget(query: LocationQuery): RouteLocationRaw {
  const defaultPath = "/";
  const rawRedirect = (query.redirect as string) || defaultPath;
  try {
    const resolved = router.resolve(rawRedirect);
    return { path: resolved.path, query: resolved.query };
  } catch {
    return { path: defaultPath };
  }
}

function checkCapsLock(event: KeyboardEvent) {
  if (event instanceof KeyboardEvent) {
    isCapsLock.value = event.getModifierState("CapsLock");
  }
}

const emit = defineEmits(["update:modelValue"]);
function toOtherForm(type: "register" | "resetPwd") {
  emit("update:modelValue", type);
}
</script>

<style lang="scss" scoped>
/* ✅ 自定义输入框样式 */
::v-deep(.custom-input) {
  width: 100%;
  height: 48px;
  background-color: rgba(141, 141, 141, 0.05) !important;
  background: red;
  border-radius: 23px;
  border: none;
  box-shadow: none;
  padding: 0;
}

::v-deep(.custom-input .el-input__inner) {
  text-align: center; 
  background-color: transparent;
}

::v-deep(.custom-input .el-input__wrapper) {
  background-color: transparent !important;
  border: none !important;
  box-shadow: none !important;
  padding: 0 15px;
  height: 100%;
  border-radius: 23px;
}

::v-deep(.custom-input .el-input__inner) {
  border: none !important;
  box-shadow: none !important;
  background-color: transparent;
  height: 100%;
  font-size: 14px;
  color: #000;
}
</style>
