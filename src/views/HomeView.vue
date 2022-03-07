<script setup>
import HeaderSuperior from "../components/Header-Superior.vue";
import HeaderInferior from "../components/Header-Inferior.vue";
import YGallery from "../components/Y-Gallery.vue";
import FooterSimple from "../components/Footer-Simple.vue";
import { computed, onMounted, ref } from "vue";

const result = ref(null);

onMounted(async () => {
  const response = await fetch("https://api.thecatapi.com/v1/breeds", {
    "x-api-key": import.meta.env.API_KEY,
  });
  const data = await response.json();
  result.value = data;
});

const firstFour = computed(() => {
  const len = result.value ? result.value.length : 0;

  if (len) {
    const cats = [];
    const getRandomCat = () => {
      while (cats.length < 4) {
        const pickedCat = result.value[Math.floor(len * Math.random())];
        if (!cats.includes(pickedCat) && pickedCat.name !== 'Persian') {
          cats.push(pickedCat);
        }
      }
    };
    getRandomCat();

    return cats;
  } else {
    return [];
  }
});
</script>

<template>
  <HeaderSuperior />
  <HeaderInferior :firstFour="firstFour" />
  <YGallery />
  <FooterSimple />
</template>
