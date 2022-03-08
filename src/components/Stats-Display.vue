<template>
  <div class="flex flex-row items-center">
    <span v-for="(_, index) in props.status" :key="index" class="w-[60px] h-[12px] rounded-md block bg-[#544439] mx-1"></span>
    <span v-for="(_, index) in missingStats" :key="index" class="w-[60px] h-[12px] rounded-md block bg-[#E0E0E0] mx-1"></span>
  </div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  status: Number,
});

const missingStats = computed(() => {
  return 5 - props.status
})
</script>
