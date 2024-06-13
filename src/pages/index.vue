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
  <div>
    <TheLogo />

    <div py-4 />

    <TheInput v-model:value="name" placeholder="What's your name?" />
    <wd-picker v-model="value" :columns="columns" label="单列选项" @confirm="handleConfirm" />
    <div>
      <button m-3 text-sm btn :disabled="!name" @click="router.push(`/pages/hi?name=${name}`)">
        Go
      </button>
    </div>
  </div>
</template>

<route lang="yaml">
layout: home
</route>
