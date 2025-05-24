<template>
  <div class="bg-white border rounded-lg shadow-sm p-4">
    <div class="flex justify-between items-center mb-4">
      <h4 class="font-semibold text-gray-700">Time of the day</h4>
      <a href="#" class="text-sm text-blue-500 hover:underline">View all</a>
    </div>
    <canvas id="timeChart" class="w-full h-64"></canvas>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import Chart from 'chart.js/auto'

onMounted(() => {
  const ctx = document.getElementById('timeChart') as HTMLCanvasElement
  const gradient = ctx.getContext('2d')!.createLinearGradient(0, 0, 0, 300)
  gradient.addColorStop(0, '#F2F2F2')
  gradient.addColorStop(1, '#CCCCCC')

  new Chart(ctx, {
    type: 'bar',
    data: {
      labels: ['12AM', '4AM', '8AM', '12PM', '4PM', '8PM'],
      datasets: [{
        label: 'Sales',
        data: [5000, 10000, 20000, 30000, 25000, 15000],
        backgroundColor: gradient
      }]
    },
    options: {
      responsive: true,
      plugins: {
        legend: { display: false }
      },
      scales: {
        x: {
          ticks: { color: '#6B7280' },
          grid: { color: '#E5E7EB' }
        },
        y: {
          title: {
            display: true,
            text: 'Time',
            color: '#6B7280',
            font: { size: 12, weight: '600' }
          },
          ticks: {
            callback: function(value, index) {
              const labels = ['12AM', '4AM', '8AM', '12PM', '4PM', '8PM']
              return labels[index] || ''
            },
            color: '#6B7280'
          },
          grid: { color: '#E5E7EB' }
        }
      }
    }
  })
})
</script>
