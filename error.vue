<script setup>
const error = useError();
const resetError = async (error) => {
  await navigateTo('/course');
  error.value = null;
};
</script>

<template>
  <div>
    <div class="bg-indigo-900 relative overflow-hidden h-screen">
      <img
          src="https://external-preview.redd.it/4MddL-315mp40uH18BgGL2-5b6NIPHcDMBSWuN11ynM.jpg?width=960&crop=smart&auto=webp&s=b98d54a43b3dac555df398588a2c791e0f3076d9"
          class="absolute h-full w-full object-cover"/>
      <div class="inset-0 bg-black opacity-25 absolute">
      </div>
      <div class="container mx-auto px-6 md:px-12 relative z-10 flex items-center py-16 xl:py-26">
        <div class="w-full font-mono flex flex-col items-center relative z-10">
          <h1 class="font-extrabold text-5xl text-center text-white leading-tight mt-4">
            {{ error.message }}
          </h1>
          <p class="font-extrabold text-8xl mt-20 text-white animate-bounce">
            404
          </p>
          <button @click="resetError" class="py-4 px-8 bg-gray-50 text-gray-950 mt-8">
              Go to the course
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

