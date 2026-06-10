<template>
  <canvas ref="chartRef"></canvas>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue'
import Chart from 'chart.js/auto'

const props = defineProps({
  records: Array
})

const chartRef = ref(null)
let chartInstance = null

function renderChart() {
  if (!props.records.length) return

  // ① 所有日期（共用 X 軸）
  const labels = [...new Set(props.records.map(r => r.record_date))]
    .sort()

  // ② 分組 service
  const grouped = {}

  props.records.forEach(r => {
    if (!grouped[r.service_name]) {
      grouped[r.service_name] = {}
    }
    grouped[r.service_name][r.record_date] = r.price
  })

  // ③ 每個 service 一條線（對齊 labels）
  const datasets = Object.keys(grouped).map((service, i) => {
    return {
      label: service,
      data: labels.map(date => grouped[service][date] ?? null),
      borderColor: getColor(i),
      spanGaps: true, // 🔥 讓 null 不斷線
      tension: 0.3
    }
  })

  if (chartInstance) chartInstance.destroy()

  chartInstance = new Chart(chartRef.value, {
    type: 'line',
    data: {
      labels,
      datasets
    }
  })
}

// 🎨 顏色產生器
function getColor(i) {
  const colors = [
    '#e53e3e',
    '#3182ce',
    '#38a169',
    '#d69e2e',
    '#805ad5',
    '#dd6b20'
  ]
  return colors[i % colors.length]
}

onMounted(renderChart)
watch(() => props.records, renderChart, { deep: true })
</script>