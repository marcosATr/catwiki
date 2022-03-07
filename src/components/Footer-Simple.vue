<template>
  <div class="bg-black container mx-auto rounded-t-3xl">
    <div class="w-full h-full px-24 py-4">
      <nav>
        <RouterLink to="/">
          <img alt="Logo catwiki" src="/img/logo.svg" />
        </RouterLink>
      </nav>
    </div>
  </div>
</template>

<script setup>
import { RouterLink } from "vue-router";
</script>
