<script setup lang="ts">
defineProps<{
  title: string;
}>();
</script>

<template>
  <div class="w-full h-16 flex items-center justify-center bg-green-800">
    <h1 class="font-bold text-3xl text-white cursor-pointer">{{ title }}</h1>
  </div>
</template>
