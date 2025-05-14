<template>
  <div class="dashboard-container">
      <div style="height:210px;margin:0 10px;height: 210px;display: flex;flex-direction: row;justify-content: space-between;align-items: center;color:#FFFFFF;margin-top:20px;">
        <div style="background:#2B66EC;display: flex;align-items: center;justify-content: space-between;border-radius: 20px;padding:28px 25px; width: 100%;height: 100%;margin: 10px;">
          <div style="margin: 10px; display: flex;flex-direction: column;">
            <span>在线设备/台</span>
            <span style="font-size:68px;">562486</span>
            <div style="display:flex;align-items: center;">
              <span style="font-size:20px;margin-right:8px;">较昨日+3.14％</span>
              <el-image style="width: 10px; height: 15px" :src="whiteUp"/>
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
            <div style="display:flex;align-items: center;">
              <span style="color:#FD6466;font-size:20px;margin-right:8px;">较昨日+3.14％</span>
              <el-image style="width: 10px; height: 15px" :src="redDown"/>
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
      <div style="height:286px;margin:20px 10px 0 10px;display: flex;background: #FFFFFF; ">
        <div style="width:580px;height:280px;background:#f5f8fd;border-bottom-right-radius: 20px;"> 
          <div style="background: #FFFFFF;width:550px;height:260px;margin-right: 20px;margin-left: 10px;    border-top-left-radius: 20px;
    border-top-right-radius: 20px;border-bottom-right-radius: 20px;text-align:center;line-height: 280px;">
            图表
          </div>
        </div>
        <div style="width: 100%;">
          <div style="background: rgb(245, 248, 253);">
            <div style="width: 100%;display: flex;justify-content: space-between;    padding: 10px; background:#fff;    border-top-left-radius: 20px;border-top-right-radius: 20px;">
              <div style="color:#333333;font-size:20px;display: flex;align-items: center;">
                <span style="font-weight:800;color:#333333;">用户地区分布</span>
                <span style="margin-left:20px;margin-right:12px;color:#6E7CE5;font-weight:800;">广东</span>
                <el-icon color="#6E7CE5"><ArrowRight /></el-icon>
              </div>
              <div style="color:#333333;display: flex;    align-items: center;">
                <span style="margin-left:12px;">全国占比</span>
                <div style="background-color: rgba(110, 124, 229, 0.2);color:#6E7CE5;border-radius: 14px;    padding: 0 10px;line-height: 30px;    margin-left: 12px;">56.8％</div>
              </div>
            </div>
          </div>

          <div class="scroll-container" style="height:210px; overflow: hidden;">
  <div class="scroll-wrap">
    <div v-for="item in cityList" style="
      font-weight: 800;     
      font-size: 16px;
      text-align: center;
      line-height: 26px; 
      color: #6E7CE5; 
      border: 1px solid #6E7CE5; 
      width: auto; 
      margin: 10px; 
      margin-bottom: 13px;
      border-radius: 30px;
      padding: 0 12px;
    "> {{ item }}</div>
  </div>
   <div class="gradient-mask"></div>
</div>


        </div>
      </div>


      <div style="height:230px;margin:10px;margin-top:0;background: #FFFFFF;">
        <div></div>
      </div>

  </div>
</template>

<script setup lang="ts">
import onlineDeviceImg from "@/assets/images/online_device@2x.png";
import activateToday from "@/assets/images/activate_today2x.png";
import whiteUp from "@/assets/images/white_up@2x.png"
import redDown from "@/assets/images/red_down@2x.png"


const cities = [
  '广州', '深圳', '上海', '北京', '杭州', '成都',
  '南京市', '西安市', '重庆市', '哈尔滨', '苏州市',
  '沈阳', '青岛', '福州', '厦门', '郑州', '武汉市'
]

const cityList = ref([])

onMounted(() => {
  cityList.value = Array.from({ length: 120 }).map(() => {
    const city = cities[Math.floor(Math.random() * cities.length)]
    const percent = (Math.random() * 50 + 5).toFixed(1) + '％'
    return `${city}市 ${percent}`
  })
})
</script>

<style lang="scss" scoped>
  .locationItem{
   
  }
  .scroll-container {
    height: 230px;
    overflow: hidden;
    position: relative;
  }

  .scroll-wrap {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    height: 100%;
    overflow-y: auto;
    padding-right: 6px; /* 给滚动条腾点空间 */
    padding-bottom: 30px;
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
