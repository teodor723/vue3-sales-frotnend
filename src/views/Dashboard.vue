<template>
  <div class="p-6 space-y-6">
    <div class="flex flex-wrap items-center gap-3 justify-between">
      <div class="flex items-center gap-2">
        <select class="border border-gray-300 rounded px-3 py-2 text-sm">
          <option>Select store</option>
        </select>
        <button class="text-xs border rounded px-3 py-2 text-gray-600 hover:bg-gray-100">
          COMPARE BRANCHES
        </button>
      </div>
      <input type="date" class="border rounded px-3 py-2 text-sm text-gray-600" value="2025-05-20" />
    </div>

    <div>
      <h2 class="text-lg font-semibold mt-4">Net sales</h2>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-2">
        <StatsCard
          v-for="(item, i) in stats"
          :key="'net-' + i"
          :icon="item.icon"
          :title="item.title"
          :value="item.value"
          :color="item.color"
        />
      </div>
    </div>

    <div>
      <h2 class="text-lg font-semibold mt-6">Gross sales</h2>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-2">
        <StatsCard
          v-for="(item, i) in stats"
          :key="'gross-' + i"
          :icon="item.icon"
          :title="item.title"
          :value="item.value"
          :color="item.color"
        />
      </div>
    </div>

    <TimeChart />
  </div>
</template>

<script setup lang="ts">
import StatsCard from '../components/StatsCard.vue'
import TimeChart from '../components/TimeChart.vue'

const stats = [
  { icon: 'calendar', title: 'Net sales', value: '$185,454.25', color: 'bg-[#E6F4EA] text-[#2E7D32]' },
  { icon: 'dollar', title: 'Avg. Ticket', value: '$978.52', color: 'bg-[#FFF3E0] text-[#EF6C00]' },
  { icon: 'user', title: 'Guests', value: '189', color: 'bg-[#E3F2FD] text-[#1565C0]' },
  { icon: 'table', title: 'Tables', value: '60', color: 'bg-[#EDE7F6] text-[#6A1B9A]' }
]
</script>
