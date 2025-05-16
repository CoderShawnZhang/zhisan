<template>
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
</template>


<script setup lang="ts">
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