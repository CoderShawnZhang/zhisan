<template>
  <div
    style="display:flex;flex-direction:column;justify-content:center;align-items:center;margin:24px;margin-bottom: 100px;"
  >
    <div style="background:#fff;height:324px;width:100%;border-radius: 20px;padding:20px;">
      <Top/>
    </div>
    <div class="wrapUcenter">
      <div class="left">
        <div class="left_l">
          <div class="left_lt">
            <div class="left_lt_l">
              <LeftLbL/>
            </div>
            <div class="left_lt_r">
              <LeftLbR/>
            </div>
          </div>
          <div class="left_lb">
            <div class="left_lb_l">
              <LeftLtL/>
            </div>
            <div class="left_lb_r">
              <LeftLtR/>
            </div>
          </div>
        </div>
      </div>
      <div class="right">
        <Right/>
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
import LeftLbL from "./components/left_lb_l.vue";
import LeftLbR from "./components/left_lb_r.vue";
import LeftLtL from "./components/left_lt_l.vue";
import LeftLtR from "./components/left_lt_r.vue";
import Right from "./components/right.vue";
import Top from "./components/top.vue";


</script>
<style scoped>
.wrapUcenter {
  display: flex;
  width: 100%;
  height: 422px; /* 固定容器高度 */
  gap: 20px;
}

.left {
 margin-top:20px;
  width: 61.5%; /* 左右宽度比例 */
  height: 100%; /* 铺满container高度 */
  box-sizing: border-box;
  display: flex; /* 这里让 left 本身也是 flex 容器 */
  flex-direction: column; /* 左侧子元素上下排列 */
}

.left_l {
  flex: 1; /* 让left_l撑满left */
  display: flex;
  flex-direction: column; /* 上下两个块垂直 */
}

.left_lt,
.left_lb {
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
}

.left_lt {
margin-bottom: 20px;
  height:246px;

      width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.left_lb {
  height:156px;

        width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}



.left_lt_l{
  width:49%;
  height:246px;
  background:#fff;
  margin-right:10px;
  border-radius: 20px;padding:20px;
}

.left_lt_r{
  width:49%;
  height:246px;
  background:#fff;
  margin-left:10px;
  border-radius: 20px;padding:20px;
}

.left_lb_l{
  width:100%;
    height:156px;
    background:#fff;
  margin-right:10px;
  border-radius: 20px;padding:20px;
}
.left_lb_r{
   width:100%;
    height:156px;
     background:#fff;
  margin-left:10px;
  border-radius: 20px;padding:20px;
}

.right {
  margin-top:20px;
  width: 38.5%;
  background-color:#fff;
  height: 100%; /* 铺满container高度 */
  display: flex;
  border-radius: 20px;padding:20px;
}
</style>
