<template>
  <div>
    
    <div style="margin: 20px 20px 10px 20px;
    padding: 10px;
    border-radius: 20px;
    background: #fff;height: calc(100vh - 130px);overflow-y:auto;">

     <div style="margin:20px;position: relative;ckground:#fff;height:40px;width:503px;border:1px solid #6E7CE5;border-radius:30px;padding: 0 10px;display: flex;align-items: center;">
        <el-input v-model="input" class="custom-input" />
        <div class="searchBtn">搜索</div>
        <div style="height:40px;width:40px;background:#4A5BDE;border-radius:50px;position: absolute;right: -60px;    display: flex;justify-content: center;align-items: center;">
          <el-image :src="searchMore" style="width:22px;height:21px;"/>
        </div>
      </div>

    <el-table
      :data="tableData"
      :border="parentBorder"
      :preserve-expanded-content="preserveExpanded"
      style="width: 100%"
      row-key="id"
      :expand-row-keys="expandRowKeys"
    >
      <el-table-column type="expand">
        <template #default="{ row }">
          <div style="width: 100%;display: flex;justify-content: space-around;border:1px solid #6E7CE5;border-radius: 4px">
              <div>姓名：雷霆震怒</div>
              <div>ID：666666</div>
              <div>段位：秀才</div>
              <div>绑定手机号码：13822222222 解绑</div>
              <el-link :underline="false" @click="toggleExpand(row)" style="color:#4A5BDE;">收起</el-link>
          </div>
        </template>
      </el-table-column>

      <el-table-column label="序列号" prop="date" />
      <el-table-column label="IP地址" prop="name" />
      <el-table-column label="型号" prop="name" />
      <el-table-column label="版本" prop="name" />
      <el-table-column label="状态" prop="state" >
        <template #default="scope">
           <el-tag v-if="scope.row.state==1" type="success">在线</el-tag>
           <el-tag v-if="scope.row.state==2" type="danger">离线</el-tag>
        </template>
      </el-table-column>
      <el-table-column label="运行时长/天" prop="name" />
      <el-table-column label="操作" min-width="70">
        <template #default="{ row }">
          <el-button
            link
            type="primary"
            size="small"
            @click="toggleExpand(row)"
          >
            详细信息
          </el-button>
          <el-button link type="danger" size="small">删除</el-button>
        </template>
      </el-table-column>
      <el-table-column type="selection" width="55">
      <template #header>
        <span>全选</span>
      </template>
    </el-table-column>
    </el-table>
    </div>
    <div style="width:100%;    display: flex;justify-content: center;">
       <el-pagination background  layout="prev, pager, next, jumper" :total="1000" />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import searchMore from "@/assets/images/searchMore@2x.png";

const parentBorder = ref(false)
const childBorder = ref(false)
const preserveExpanded = ref(false)
const expandRowKeys = ref<number[]>([])
const tableData = []

for (let i = 1; i <= 100; i++) {
  tableData.push({
    id: i,
    date: `2016-05-${String((i % 30) + 1).padStart(2, '0')}`,
    name: `用户-${i}`,
    state: i % 3, // 0 / 1 / 2 三种状态轮换
    city: 'San Francisco',
    address: `No.${i} 21st St, San Francisco`,
    zip: 'CA 94114',
    family: [
      {
        name: `Jerry-${i}`,
        state: 'California',
        city: 'San Francisco',
        address: `${i}-A 21st St`,
        zip: 'CA 94114',
      },
      {
        name: `Spike-${i}`,
        state: 'California',
        city: 'San Francisco',
        address: `${i}-B 21st St`,
        zip: 'CA 94114',
      },
      {
        name: `Tyke-${i}`,
        state: 'California',
        city: 'San Francisco',
        address: `${i}-C 21st St`,
        zip: 'CA 94114',
      },
    ],
  })
}

// 手动切换展开状态
const toggleExpand = (row: any) => {
  const index = expandRowKeys.value.indexOf(row.id)
  if (index > -1) {
    expandRowKeys.value.splice(index, 1)
  } else {
    expandRowKeys.value.push(row.id)
  }
}

</script>

<style lang="scss" scoped>
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