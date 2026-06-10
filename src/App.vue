<template>

  <Header />

  <RecordForm
    @add-record="addRecord"
  />

  <RecordTable
    :records="records"
  />

</template>

<script setup>

import { ref, onMounted } from 'vue'

import Header from './components/Header.vue'
import RecordForm from './components/RecordForm.vue'
import RecordTable from './components/RecordTable.vue'

const records = ref([])

async function fetchRecords() {

  const res = await fetch('/api/records')

  records.value = await res.json()

}

function addRecord(data) {

  records.value.push(data)

}

onMounted(() => {

  fetchRecords()

})

</script>