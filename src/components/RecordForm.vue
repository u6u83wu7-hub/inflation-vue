<template>
  <form @submit.prevent="submit">

    <label>服務</label>
    <select v-model="service_name">
      <option>Netflix 高級方案</option>
      <option>Spotify 家庭方案</option>
      <option>YouTube Premium 家庭方案</option>
    </select>

    <label>價格</label>
    <input type="number" v-model="price" />

    <label>日期</label>
    <input type="month" v-model="record_date" />

    <button>新增</button>

  </form>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add-record'])

const service_name = ref('')
const price = ref('')
const record_date = ref('')

function submit() {
  emit('add-record', {
    service_name: service_name.value,
    price: Number(price.value),
    record_date: record_date.value
  })
}
</script>