<template>
  <div>hi</div>
</template>
<script setup>
import { useRoute } from "vue-router";
  const route = useRoute();
  const params = route.params;
  console.log(params);
</script>
