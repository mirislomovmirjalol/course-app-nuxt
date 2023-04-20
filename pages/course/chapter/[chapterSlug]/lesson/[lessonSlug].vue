<script setup>
const course = useCourse();
const route = useRoute();

const chapter = computed(() => {
  return course.chapters.find(
      (chapter) => chapter.slug === route.params.chapterSlug
  );
});
const lesson = computed(() => {
  return chapter.value.lessons.find(
      (lesson) => lesson.slug === route.params.lessonSlug
  );
});
</script>
<template>
  <div>
    <h3>Chapter slug: {{ chapter.title }}</h3>
    <h3>Lesson slug: {{ lesson.title }}</h3>
  </div>
</template>