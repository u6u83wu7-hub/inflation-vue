<template>
  <Header />

  <RecordForm @add-record="addRecord" />

  <InflationChart :records="records" />

  <RecordTable :records="records" />
</template>

<script setup>

import { ref } from 'vue'

import Header from './components/Header.vue'
import RecordForm from './components/RecordForm.vue'
import RecordTable from './components/RecordTable.vue'
import InflationChart from './components/InflationChart.vue'

const records = ref([

  // =========================
  // Netflix（高級方案）
  // =========================
  { service_name: "Netflix 高級方案", price: 390, record_date: "2016-01" },
  { service_name: "Netflix 高級方案", price: 390, record_date: "2023-01" },
  { service_name: "Netflix 高級方案", price: 460, record_date: "2024-01" },
  { service_name: "Netflix 高級方案", price: 460, record_date: "2025-01" },

  // =========================
  // YouTube Premium（家庭）
  // =========================
  { service_name: "YouTube Premium 家庭方案", price: 269, record_date: "2019-01" },
  { service_name: "YouTube Premium 家庭方案", price: 399, record_date: "2024-01" },
  { service_name: "YouTube Premium 家庭方案", price: 479, record_date: "2025-01" },

  // =========================
  // Spotify（家庭 / Family）
  // =========================
  { service_name: "Spotify 家庭方案", price: 240, record_date: "2021-01" },
  { service_name: "Spotify 家庭方案", price: 268, record_date: "2023-01" },
  { service_name: "Spotify 家庭方案", price: 298, record_date: "2025-01" }

])

function addRecord(data) {
  records.value.push(data)
}

</script>