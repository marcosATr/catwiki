<script setup>
import { RouterView } from "vue-router";
import NavStatic from "./components/Nav-Static.vue";
</script>

<template>
  <NavStatic />
  <RouterView />
  <!-- <Suspense>
    <template #default>
      <RouterView />
    </template>
    <template #fallback>
      <span>Loading...</span>
    </template>
  </Suspense> -->
</template>

<style></style>
