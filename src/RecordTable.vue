<template>

<table>

<thead>
<tr>
<th>服務名稱</th>
<th>價格</th>
<th>日期</th>
</tr>
</thead>

<tbody>

<tr
v-for="item in records"
:key="item.id"
>

<td>{{ item.service_name }}</td>
<td>{{ item.price }}</td>
<td>{{ item.record_date }}</td>

</tr>

</tbody>

</table>

</template>

<script setup>

defineProps({
  records:Array
})

</script>