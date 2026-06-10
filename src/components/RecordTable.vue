<template>
  <table>
    <thead>
      <tr>
        <th>服務</th>
        <th>價格</th>
        <th>日期</th>
      </tr>
    </thead>

    <tbody>
      <tr v-for="(item, i) in records" :key="i">
        <td>{{ item.service_name }}</td>
        <td>{{ item.price }}</td>
        <td>{{ item.record_date }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
defineProps({
  records: Array
})
</script>