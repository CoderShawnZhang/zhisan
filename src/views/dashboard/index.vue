<template>
  <div class="dashboard-container">
      <div style="height:210px;margin:0 10px;height: 210px;display: flex;flex-direction: row;justify-content: space-between;align-items: center;color:#FFFFFF;margin-top:20px;">
        <div style="background:#2B66EC;display: flex;align-items: center;justify-content: space-between;border-radius: 20px;padding:28px 25px; width: 100%;height: 100%;margin: 10px;">
          <div style="margin: 10px; display: flex;flex-direction: column;">
            <span>在线设备/台</span>
            <span style="font-size:68px;">562486</span>
            <div>
              <span style="font-size:20px;">较昨日+3.14％</span>
              <span>|</span>
            </div>
          </div>
          <div style="background:#fff;height: 52px;width: 52px;border-radius: 30px;display: flex;justify-content: center;align-items: center;">
            <el-image style="width: 40px; height: 40px" :src="onlineDeviceImg"/>
          </div>
        </div>

        <div style="background:#35CF96;display: flex;align-items: center;justify-content: space-between;border-radius: 20px;padding:28px 25px; width: 100%;height: 100%;margin: 10px;">
          <div style="margin: 10px; display: flex;flex-direction: column;">
            <span>今日激活数量/台</span>
            <span style="font-size:68px;">562486</span>
            <div>
              <span style="color:#FD6466;font-size:20px;">较昨日+3.14％</span>
              <span>|</span>
            </div>
          </div>
          <div style="background:#fff;height: 52px;width: 52px;border-radius: 30px;display: flex;justify-content: center;align-items: center;">
            <el-image style="width: 35px; height: 40px" :src="activateToday"/>
          </div>
        </div>

        <div style="background: linear-gradient( 134deg, #FEC637 0%, #FFF153 100%);display: flex;align-items: center;justify-content: space-between;border-radius: 20px;padding:28px 25px; width: 100%;height: 100%;margin: 10px;">
          <div style="margin: 10px; display: flex;flex-direction: column;">
            <span>总台数/台</span>
            <span style="font-size:68px;">562486</span>
          </div>
        </div>

      </div>
      <div style="height:286px;margin:10px 10px 0 10px;display: flex;background: #FFFFFF;">
        <div style="width:580px;height:280px;background:#f5f8fd;border-bottom-right-radius: 20px;"> 
          <div style="background: #FFFFFF;width:560px;height:260px;    border-bottom-right-radius: 20px;">
            123123123
          </div>
        </div>
        <div>
          222222
        </div>
      </div>


      <div style="height:230px;margin:10px;margin-top:0;background: #FFFFFF;">
        <div></div>
      </div>

  </div>
</template>

<script setup lang="ts">
import onlineDeviceImg from "@/assets/images/online_device@2x.png";
import activateToday from "@/assets/images/activate _today2x.png";
</script>

<style lang="scss" scoped>

</style>
