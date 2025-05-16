<template>
  <div class="contain">

    <!--搜索-->
    <div style="display: flex;justify-content: space-between;align-items: center;">
       <SearchInput/>
      <div style="width:147px;height:40px;border: 1px solid #4A5BDE;border-radius: 20px;color:#4A5BDE;line-height:40px;text-align:center;">
        历史记录
      </div>
    </div>
    <!--内容-->
    <div style="margin-top: 24px;">
      <!--上部分-->
      <div>
        <div style="color:#333333;font-size:20px;font-weight:800;">用户详细信息</div>
        <div style="display: flex;width: 100%;justify-content: space-between;padding-right: 80px;margin-top: 8px;">
          <div><span style="font-size:16px;color:#333333;font-weight: 800;">姓名</span><span>：皇甫嘉欣</span>
          <span style="cursor: pointer;margin-left:20px;color:#6E7CE5;" @click="popDialogName()">修改</span></div>
          <div><span style="font-size:16px;color:#333333;font-weight: 800;">段位</span><span>：秀才</span>
          <span style="cursor: pointer;margin-left:20px;color:#6E7CE5;" @click="popDialogLevel()">修改</span></div>
          <div><span style="font-size:16px;color:#333333;font-weight: 800;">绑定手机号码</span><span>：13137589630</span>
          <span style="cursor: pointer;margin-left:20px;color:#6E7CE5;" @click="popDialogPhone()">修改</span></div>
          <div><span style="font-size:16px;color:#333333;font-weight: 800;">ID</span><span>：666666</span></div>
          <div><span style="font-size:16px;color:#333333;font-weight: 800;">状态</span><span>：在线</span></div>
        </div>
        <div style="display:flex;margin-top: 12px;">
          <div><span style="font-size:16px;color:#333333;font-weight: 800;">地址</span><span>：河南省 周口市 太康县 朱口镇 大石村</span></div>
          <div><span style="font-size:16px;color:#333333;font-weight: 800;margin-left:88px;">年级</span><span>：一年级</span></div>
        </div>
      </div>
      <!--下部分-->
      <div style="display:flex;justify-content: space-between;margin-top:24px;">
        <div style="width: 100%;display: flex;flex-direction: column;">
            <div style="color:#333333;font-size:20px;font-weight:800;">用户设备信息</div>
            <div style="display: flex;justify-content: space-between;width: 100%;margin-top: 8px;">
              <div style="display:flex;flex-direction: column;    align-items: center;">
                <span style="color:#333333;font-size:20px;font-weight:400px;">序列号</span>
                <span style="margin-top:10px;color:#666666;">X001</span>
              </div>
              <div style="display:flex;flex-direction: column;align-items: center;">
                <span style="color:#333333;font-size:20px;font-weight:400px;">IP地址</span>
                <span style="margin-top:10px;color:#666666;">00-50-56-C0-00-08</span>
              </div>
              <div style="display:flex;flex-direction: column;align-items: center;">
                <span style="color:#333333;font-size:20px;font-weight:400px;">型号</span>
                <span style="margin-top:10px;color:#666666;">x-1086</span>
              </div>
              <div style="display:flex;align-items: flex-end;">
                <div style="display:flex;flex-direction: column;align-items: center;">
                  <span style="color:#333333;font-size:20px;font-weight:400px;">版本</span>
                  <div style="display:flex;    align-items: center;margin-top:10px;">
                    <div style="color:#666666;">V.0.01 未更新</div>
                  </div>
                </div>
                <div style="margin-bottom: 2px;">
                  <div style="border-radius: 4px;margin-left:12px;width:62px;height:22px;background-color: rgba(74, 91, 222, 0.2);color:#4A5BDE;font-size:12px;    text-align: center;line-height: 22px;">更新推送</div>
                </div>
              </div>
              
            </div>
        </div>
        <div style="display: flex;flex-direction: column;align-items: center;margin-left: 180px;width: 200px;justify-content: center;font-size:16px;">
          <div><el-image :src="logo" style="width:48px;height:48px"/></div>
          <span style="color:#666666;">用户头像</span>
          <span style="color:#4A5BDE;">更改</span>
        </div>
      </div>
    </div>

    <!--修改姓名-->
    <el-dialog v-model="dialogUpdateName" width="628px" :show-close="false" align-center style="border-radius: 20px;">
      <div style="height:249px;width:100%;display:flex;flex-direction:column;align-items: center;justify-content: center;">
        <div style="margin-bottom:12px;background:#F1F1F1;height:40px;width:372px;border-radius:30px;padding: 0 10px;display: flex;align-items: center;">
          <el-input v-model="input" class="custom-input" />
        </div>
        <div style="display: flex;width: 100%;justify-content: center;margin-top:12px;">
          <div> <el-button style="width:372px;height: 40px;border-radius: 20px;background:#4A5BDE;color:#fff;">修改</el-button></div>
        </div>
      </div>
    </el-dialog>

    <!--修改段位-->
    <el-dialog v-model="dialogUpdateLevel" width="628px" :show-close="false" align-center style="border-radius: 20px;">
      <div style="height:249px;width:100%;display:flex;flex-direction:column;align-items: center;justify-content:center;">
        <div style="height:229px;width:100%;display:flex;flex-direction:column;align-items: center;justify-content: space-around;color:#fff;">
            <div style="display:flex;width:500px;justify-content:space-between;">
              <span style="width:130px;height:40px;border-radius:20px;color:#fff;background:#4A5BDE;text-align:center;line-height:40px;">秀才</span>
              <span style="width:130px;height:40px;border-radius:20px;color:#666666;background:#F1F1F1;text-align:center;line-height:40px;">举人</span>
              <span style="width:130px;height:40px;border-radius:20px;color:#666666;background:#F1F1F1;text-align:center;line-height:40px;">榜眼</span>
            </div>
             <div style="display:flex;width:320px;justify-content:space-between;">
              <span style="width:130px;height:40px;border-radius:20px;color:#666666;background:#F1F1F1;text-align:center;line-height:40px;">探花</span>
              <span style="width:130px;height:40px;border-radius:20px;color:#666666;background:#F1F1F1;text-align:center;line-height:40px;">状元</span>
            </div>
            <div style="color:#4A5BDE;display:flex;width:335px;justify-content:space-between;">
              <span style="height:40px;width:40px;border:1px solid #4A5BDE;border-radius:20px;text-align:center;line-height:40px;">1星</span>
              <span style="height:40px;width:40px;color:#666666;border-radius:20px;text-align:center;line-height:40px;">2星</span>
              <span style="height:40px;width:40px;color:#666666;border-radius:20px;text-align:center;line-height:40px;">3星</span>
            </div>
            <div style="display: flex;width: 100%;justify-content: center;margin-top:12px;">
              <div> <el-button style="width:372px;height: 40px;border-radius: 20px;background:#4A5BDE;color:#fff;">修改</el-button></div>
            </div>
        </div>
      </div>
    </el-dialog>

    <!--修改绑定手机号码-->
    <el-dialog v-model="dialogUpdatePhone" width="628px" :show-close="false" align-center style="border-radius: 20px;">
      <div style="height:249px;width:100%;display:flex;flex-direction:column;align-items: center;justify-content: center;">
        <div style="margin-bottom:12px;background:#F1F1F1;height:40px;width:372px;border-radius:30px;padding: 0 10px;display: flex;align-items: center;">
          <el-input v-model="input" class="custom-input" />
        </div>
        <div style="display: flex;width: 372px;justify-content: space-between;margin-top:12px;">
          <div> <el-button style="width:166px;height: 40px;border-radius: 20px;background:#4A5BDE;color:#fff;">解绑</el-button></div>
          <div> <el-button style="width:166px;height: 40px;border-radius: 20px;background:#4A5BDE;color:#fff;">修改</el-button></div>
        </div>
      </div>
    </el-dialog>
  </div>
</template>

<script lang="ts" setup>
import logo from "@/assets/logo@2x.png";
import searchMore from "@/assets/images/searchMore@2x.png";
import SearchInput from "@/components/SearchInput/index.vue"

const dialogUpdateName = ref(false)//弹出修改姓名
const dialogUpdateLevel = ref(false)//弹出修改段位
const dialogUpdatePhone = ref(false)//弹出修改手机号

const input = ref("aaaa")
defineProps({
  collapse: {
    type: Boolean,
    required: true,
  },
});

function popDialogName(){
  dialogUpdateName.value = true
}
function popDialogLevel(){
  dialogUpdateLevel.value = true
}
function popDialogPhone(){
  dialogUpdatePhone.value = true
}
</script>

<style lang="scss" scoped>
  .contain{
    display:flex;
    flex-direction:column;
  }

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
    text-align: center;
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
  }

</style>
