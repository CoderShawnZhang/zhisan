<template>
	<div class="wrapCount">
        <div style="width:100%;height:210px;display:flex;    padding: 10px;">
	        <div class="onlineDevice">
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

	        <div class="activateToday">
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

	        <div class="total">
	          <div style="margin: 10px; display: flex;flex-direction: column;">
	            <span>总台数/台</span>
	            <span style="font-size:68px;">562486</span>
	          </div>
	        </div>
        </div>
      </div>
</template>

<script setup lang="ts">
	//引入图片
	import onlineDeviceImg from "@/assets/images/online_device@2x.png";
	import activateToday from "@/assets/images/activate_today2x.png";
	import whiteUp from "@/assets/images/white_up@2x.png"
	import redDown from "@/assets/images/red_down@2x.png"
</script>

<style scoped lang="scss">
	.wrapCount{
		height: 210px;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		color:#FFFFFF;
	}

	.wrapCount .onlineDevice{
		background:#2B66EC;
		display: flex;
		align-items: center;
		justify-content: space-between;
		border-radius: 20px;
		padding:28px 25px; 
		width: 100%;
		height: 100%;
		margin: 10px;
	}
	.wrapCount .activateToday{
		background:#35CF96;
		display: flex;
		align-items: center;
		justify-content: space-between;
		border-radius: 20px;
		padding:28px 25px; 
		width: 100%;
		height: 100%;
		margin: 10px;
	}
	.wrapCount .total{
		background: linear-gradient( 134deg, #FEC637 0%, #FFF153 100%);
		display: flex;
		align-items: center;
		justify-content: space-between;
		border-radius: 20px;
		padding:28px 25px; 
		width: 100%;
		height: 100%;
		margin: 10px;
	}
</style>