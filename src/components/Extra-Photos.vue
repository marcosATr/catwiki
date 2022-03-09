<template>
  <div class="md:container mx-auto">
    <div class="w-full h-full px-8 md:px-24 py-16">
      <div class="w-full py-8">
        <span class="font-semibold text-2xl">Other Photos</span>
      </div>

      <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
        <div v-for="(photo, index) in catPhotos" :key="index" class="photoItem md:max-w-[278px] md:max-h-[278px]">
          <img :alt="photo.breeds[0].name" :src="photo.url" class="w-full h-full object-cover rounded-xl" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.photoItem {
  @media (max-width: 768px) {
    height: calc(100vw / 2 - 30px);
    width: calc(100vw / 2 - 30px);
  }
}
</style>

<script setup>
import { onMounted, ref } from "vue";

const props = defineProps({
  id: String,
});

const catPhotos = ref(null);

onMounted(async () => {
  const response = await fetch(`https://api.thecatapi.com/v1/images/search?limit=4&breed_id=${props.id}`, {
    "x-api-key": import.meta.env.API_KEY,
  });
  const data = await response.json();
  catPhotos.value = data;
});
</script>
