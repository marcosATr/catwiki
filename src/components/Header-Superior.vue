<template>
  <div class="md:container mx-auto">
    <div class="w-full h-full px-8 md:px-24 py-16 bg-black rounded-t-3xl md:min-h-[600px] flex items-center bg-[url('/img/HeroImagelg.png')] bg-[position:60%] md:bg-[position:50%]">
      <div class="w-full md:w-[50%] h-full flex">
        <div class="max-w-[380px] text-white h-full flex flex-col">
          <img alt="Logo catwiki" src="/img/logo.svg" class="w-[80%]" />
          <span class="py-6 text-2xl">Get to know more about any cat breed!</span>
          <div class="w-full relative" ref="box">
            <input class="bg-white text-black text-sm p-4 w-full rounded-full my-4" v-model="breedSearchString" placeholder="Search any breed" @click="() => handleInputClick()" />
            <div v-if="isSearching" class="max-h-[204px] text-black bg-white px-1 w-full absolute rounded-md flex flex-col overflow-y-auto">
              <RouterLink :to="'/breed/' + breed.id" v-for="breed in filteredBreeds" :key="breed.id" class="bg-white hover:bg-[#f5f5f5]">
                <div class="w-full p-2 cursor-pointer">{{ breed.name }}</div>
              </RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { computed, ref } from "vue";
const box = ref(null);
const isSearching = ref(false);
const breedSearchString = ref("");

const props = defineProps({
  breeds: Array,
});

const filteredBreeds = computed(() => {
  if (isSearching.value) {
    if (breedSearchString.value) {
      const result = props.breeds.filter((breed) => breed.name.toLowerCase().includes(breedSearchString.value.toLowerCase()));
      return result;
    } else {
      return props.breeds;
    }
  } else {
    return [];
  }
});

function handleInputClick() {
  isSearching.value = true;
  document.addEventListener("mousedown", handleClickOutside);
}
function handleClickOutside() {
  const e = window.event;
  //does the box contain the target of the event?
  const contains = box.value.contains(e.target);
  const equals = box.value === e.target;

  if (contains === false && equals === false) {
    console.log("removed menu");
    isSearching.value = false;
    document.removeEventListener("mousedown", handleClickOutside);
  }
}
</script>
