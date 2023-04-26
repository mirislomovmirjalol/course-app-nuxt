<script setup>
const {chapters} = useCourse();

const resetError = async (error) => {
  await navigateTo('/course');
  error.value = null;
};
</script>

<template>
  <div
      class="p-12 bg-gray-50 w-full h-full min-h-screen flex flex-col items-center"
  >
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <div
          class="prose p-8 bg-white rounded-md flex flex-col border border-gray-300"
      >
        <h3 class="text-lg font-bold">Chapters</h3>
        <div
            class="space-y-1 mb-4 flex flex-col"
            v-for="chapter in chapters"
            :key="chapter.slug"
        >
          <h4 class="font-bold mt-4">{{ chapter.title }}</h4>
          <NuxtLink
              v-for="(lesson, index) in chapter.lessons"
              :key="lesson.slug"
              class="flex flex-row space-x-1 no-underline prose-sm font-normal py-1 px-4 -mx-4 rounded-md hover:bg-gray-200"
              :to="lesson.path"
          >
            <span
                class="text-gray-500"
            >
              {{ index + 1 }}
            </span>
            <span>
              {{ lesson.title }}
            </span>
          </NuxtLink>
        </div>
      </div>

      <div
          class="prose p-8 bg-white rounded-md border border-gray-300"
      >
        <NuxtErrorBoundary>
          <NuxtPage/>
          <template #error="{ error }">
            <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative flex" role="alert">
              <p class="block sm:inline">
                {{ error.value.message }}
              </p>
              <button @click="resetError(error)" class="absolute top-0 bottom-0 right-0 px-4 py-3">
                <svg class="fill-current h-6 w-6 text-red-500" role="button" xmlns="http://www.w3.org/2000/svg"
                     viewBox="0 0 20 20"><title>Close</title>
                  <path
                      d="M14.348 14.849a1.2 1.2 0 0 1-1.697 0L10 11.819l-2.651 3.029a1.2 1.2 0 1 1-1.697-1.697l2.758-3.15-2.759-3.152a1.2 1.2 0 1 1 1.697-1.697L10 8.183l2.651-3.031a1.2 1.2 0 1 1 1.697 1.697l-2.758 3.152 2.758 3.15a1.2 1.2 0 0 1 0 1.698z"/>
                </svg>
              </button>
            </div>
          </template>
        </NuxtErrorBoundary>
      </div>
    </div>
  </div>
</template>

<style scoped>
.router-link-active {
  @apply bg-gray-200;
}
</style>