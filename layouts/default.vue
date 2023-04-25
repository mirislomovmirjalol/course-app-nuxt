<template>
  <div class="md:flex flex-col md:flex-row w-full border-b border-gray-300">
    <div @click="open"
         class="flex flex-col w-full md:w-64 text-gray-700 bg-white dark-mode:text-gray-200 dark-mode:bg-gray-800 flex-shrink-0">
      <div class="flex-shrink-0 px-8 py-4 flex flex-row items-center justify-between">
        <a href="#"
           class="text-lg font-semibold tracking-widest text-gray-900 uppercase rounded-lg dark-mode:text-white focus:outline-none focus:shadow-outline">
          Course app
        </a>
      </div>
    </div>
  </div>
  <slot/>
</template>
<script setup>
const nav = ref(false);
const open = () => {
  this.nav = !this.nav;
};
// You might choose this based on an API call or logged-in status
const layout = "default";
</script>