<template>
  <div class="md:container mx-auto bg-[#E3E1DC] rounded-b-3xl min-h-[600px]">
    <div class="w-full h-full px-8 md:px-24 py-16 flex flex-col">
      <div>
        <span class="font-medium text-xl">Most Searched Breeds</span>
        <div class="myDivider mt-4 mb-8"></div>
        <div class="flex flex-col md:flex-row md:justify-between md:items-end">
          <div><h1 class="font-semibold text-5xl md:max-w-[60%]">66+ varieties for you to discover</h1></div>
          <div class="py-4 md:py-0"><span class="font-bold text-[#74675c] uppercase">See More</span></div>
        </div>
        <div class="flex flex-wrap justify-between pt-14 catList">
          <div v-for="cat in firstFour" :key="cat.id" class="max-w-[220px] relative z-10">
            <img :alt="cat.name" :src="cat.image.url" class="rounded-xl w-[220px] h-[220px] object-cover" />
            <div class="font-semibold text-lg py-4">{{ cat.name }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  firstFour: Array,
});
</script>

<style lang="scss">
.myDivider {
  width: 60px;
  height: 3px;
  background-color: black;
  display: block;
}
.catList {
  div {
    &:first-child {
      &:before {
        content: "";
        background-color: #dec68b;
        width: 47px;
        height: 180px;
        display: block;
        position: absolute;
        margin: 25px -15px;
        border-radius: 18px;
        z-index: -1;
      }
    }
  }
}
</style>
