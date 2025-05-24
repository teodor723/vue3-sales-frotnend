<template>
  <div class="bg-white border rounded-lg shadow-sm p-4 flex items-center justify-between">
    <div class="flex items-center gap-3">
      <div
          class="w-10 h-10 flex items-center justify-center rounded-md"
          :class="color"
      >
        <component :is="iconMap[icon]" class="w-5 h-5"/>
      </div>
      <div>
        <p class="text-sm text-gray-500">{{ title }}</p>
        <p class="text-lg font-semibold">{{ value }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import {defineProps} from 'vue'
import {CalendarIcon, DollarSignIcon, UserIcon, TableIcon} from 'lucide-vue-next'

const iconMap: Record<string, any> = {
  calendar: CalendarIcon,
  dollar: DollarSignIcon,
  user: UserIcon,
  table: TableIcon
}

defineProps<{
  title: string
  value: string
  icon: 'calendar' | 'dollar' | 'user' | 'table'
  color: string
}>()
</script>
