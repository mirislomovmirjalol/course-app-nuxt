<template>
  <NuxtLayout :name="layout">
    <h1>default layout</h1>
    <slot/>
  </NuxtLayout>
</template>
<script setup>
// You might choose this based on an API call or logged-in status
const layout = "default";
</script>