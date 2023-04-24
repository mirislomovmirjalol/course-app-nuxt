<script setup>
const {chapters} = useCourse();
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
          class="prose p-8 bg-white rounded-md border border-gray-300 flex"
      >
        <NuxtPage/>
      </div>
    </div>
  </div>
</template>

<style scoped>
.router-link-active {
  @apply bg-gray-200;
}
</style>