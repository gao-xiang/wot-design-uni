<script setup lang="ts">
const name = ref('')

const columns = ref([])
const value = ref('id_card')
function handleConfirm({ value }) {
  value.value = value
}

uni.request({
  url: 'https://api.qiutuo.com.cn/sso/api/id-number/id_number_type', // 仅为示例，并非真实接口地址。
  header: {
    'content-type': 'application/json;charset=UTF-8', // 自定义请求头信息
  },
  success: (res) => {
    columns.value = res.data.data
  },
})
console.log(columns)
</script>

<template>
  <wd-picker v-model="value" :columns="columns" label="单列选项" @confirm="handleConfirm" />
</template>

<route lang="yaml">
layout: home
</route>
