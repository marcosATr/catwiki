<template>
  <div class="md:container mx-auto">
    <div class="w-full h-full py-16">
      <div class="w-full flex flex-wrap" v-if="catData">
        <div class="w-full md:w-[40%] px-8 md:pl-0">
          <img alt="" :src="catData.url" class="h-auto w-full rounded-lg object-cover" />
        </div>
        <div class="w-full md:w-[60%] px-8 md:pr-0">
          <h1 class="text-5xl font-semibold mb-8">{{ catData.breeds[0].name }}</h1>
          <p class="py-2 font-medium text-xl">{{ catData.breeds[0].description }}</p>
          <p class="py-2"><span class="font-bold text-base">Temperament</span>: {{ catData.breeds[0].temperament }}</p>
          <p class="py-2"><span class="font-bold text-base">Origin</span>: {{ catData.breeds[0].origin }}</p>
          <p class="py-2"><span class="font-bold text-base">Average Life Span</span>: {{ catData.breeds[0].life_span }}</p>
          <div>
            <div class="flex items-center">
              <div class="py-2 min-w-[150px]"><span class="font-bold text-base">Adaptability</span>:</div>
              <StatsDisplay :status="catData.breeds[0].adaptability"/>
            </div>
            <div class="flex items-center">
              <div class="py-2 min-w-[150px]"><span class="font-bold text-base">Affection</span>:</div>
              <StatsDisplay :status="catData.breeds[0].affection_level"/>
            </div>
            <div class="flex items-center">
              <div class="py-2 min-w-[150px]"><span class="font-bold text-base">Child Friendly</span>:</div>
              <StatsDisplay :status="catData.breeds[0].child_friendly"/>
            </div>
            <div class="flex items-center">
              <div class="py-2 min-w-[150px]"><span class="font-bold text-base">Grooming</span>:</div>
              <StatsDisplay :status="catData.breeds[0].grooming"/>
            </div>
            <div class="flex items-center">
              <div class="py-2 min-w-[150px]"><span class="font-bold text-base">Intelligence</span>:</div>
              <StatsDisplay :status="catData.breeds[0].intelligence"/>
            </div>
            <div class="flex items-center">
              <div class="py-2 min-w-[150px]"><span class="font-bold text-base">Health Issues</span>:</div>
              <StatsDisplay :status="catData.breeds[0].health_issues"/>
            </div>
            <div class="flex items-center">
              <div class="py-2 min-w-[150px]"><span class="font-bold text-base">Social Needs</span>:</div>
              <StatsDisplay :status="catData.breeds[0].social_needs"/>
            </div>
            <div class="flex items-center">
              <div class="py-2 min-w-[150px]"><span class="font-bold text-base">Stranger Friendly</span>:</div>
              <StatsDisplay :status="catData.breeds[0].stranger_friendly"/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import StatsDisplay from "../components/Stats-Display.vue";

const route = useRoute();
const { id } = route.params;

const catData = ref(null);
// const catPhotos = ref([]);

onMounted(async () => {
  const response = await fetch(`https://api.thecatapi.com/v1/images/search?breed_ids=${id}`, {
    "x-api-key": import.meta.env.API_KEY,
  });
  const data = await response.json();
  catData.value = data[0];
});
</script>
