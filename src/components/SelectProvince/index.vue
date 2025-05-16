<template>
  <div class="province-dropdown">
    <el-input
      v-model="selectedProvince"
      placeholder="请选择省份"
      readonly
      @click="popoverVisible = true"
      ref="inputRef"
    />

    <el-popover
      v-model:visible="popoverVisible"
      :width="300"
      trigger="click"
      placement="bottom-start"
      :virtual-ref="inputRef"
      virtual-triggering
      popper-class="province-popper"
    >
      <div class="province-selector">
        <el-input v-model="search" placeholder="搜索" clearable size="small" />
        <el-scrollbar height="260px">
          <div v-for="group in filteredGrouped" :key="group.letter" class="group">
            <div class="group-letter">{{ group.letter }}</div>
            <div
              class="province-item"
              v-for="item in group.list"
              :key="item.name"
              @click="selectProvince(item)"
            >
              {{ item.name }}
            </div>
          </div>
        </el-scrollbar>
      </div>
    </el-popover>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const inputRef = ref()
const popoverVisible = ref(false)
const search = ref('')
const selectedProvince = ref('')

// 原始数据
const provinces = [
  { name: '北京', pinyin: 'beijing' },
  { name: '上海', pinyin: 'shanghai' },
  { name: '广东', pinyin: 'guangdong' },
  { name: '浙江', pinyin: 'zhejiang' },
  { name: '江苏', pinyin: 'jiangsu' },
  { name: '福建', pinyin: 'fujian' },
  { name: '湖北', pinyin: 'hubei' },
  { name: '河南', pinyin: 'henan' },
  { name: '湖南', pinyin: 'hunan' },
  { name: '山东', pinyin: 'shandong' },
  { name: '山西', pinyin: 'shanxi' },
  { name: '四川', pinyin: 'sichuan' },
  { name: '云南', pinyin: 'yunnan' },
  { name: '贵州', pinyin: 'guizhou' },
  { name: '安徽', pinyin: 'anhui' },
  { name: '江西', pinyin: 'jiangxi' },
  { name: '河北', pinyin: 'hebei' },
  { name: '辽宁', pinyin: 'liaoning' },
  { name: '吉林', pinyin: 'jilin' },
  { name: '黑龙江', pinyin: 'heilongjiang' },
  { name: '重庆', pinyin: 'chongqing' },
  { name: '天津', pinyin: 'tianjin' },
  { name: '宁夏', pinyin: 'ningxia' },
  { name: '青海', pinyin: 'qinghai' },
  { name: '新疆', pinyin: 'xinjiang' },
  { name: '西藏', pinyin: 'xizang' },
  { name: '内蒙古', pinyin: 'neimenggu' },
  { name: '海南', pinyin: 'hainan' },
  { name: '广西', pinyin: 'guangxi' },
  { name: '香港', pinyin: 'xianggang' },
  { name: '澳门', pinyin: 'aomen' },
  { name: '台湾', pinyin: 'taiwan' }
]

// 拼音分组
const groupedProvinces = computed(() => {
  const grouped = {}
  provinces.forEach(item => {
    const letter = item.pinyin[0].toUpperCase()
    if (!grouped[letter]) {
      grouped[letter] = []
    }
    grouped[letter].push(item)
  })
  const sortedKeys = Object.keys(grouped).sort()
  return sortedKeys.map(letter => ({
    letter,
    list: grouped[letter].sort((a, b) => a.pinyin.localeCompare(b.pinyin))
  }))
})

// 搜索过滤
const filteredGrouped = computed(() => {
  const keyword = search.value.trim().toLowerCase()
  if (!keyword) return groupedProvinces.value

  const result = []
  groupedProvinces.value.forEach(group => {
    const matched = group.list.filter(
      item =>
        item.name.includes(keyword) || item.pinyin.includes(keyword)
    )
    if (matched.length > 0) {
      result.push({
        letter: group.letter,
        list: matched
      })
    }
  })
  return result
})

// 选择
const selectProvince = (item) => {
  selectedProvince.value = item.name
  popoverVisible.value = false
}
</script>

<style scoped>
.group-letter {
  font-weight: bold;
  margin: 10px 0 4px;
  color: #999;
}
.province-item {
  padding: 6px 8px;
  cursor: pointer;
  border-radius: 4px;
}
.province-item:hover {
  background-color: #f0f0f0;
}
.province-selector {
  padding: 4px;
}
</style>

<style>
/* 额外优化 popper 样式 */
.province-popper {
  padding: 6px !important;
  border-radius: 8px;
}
</style>
