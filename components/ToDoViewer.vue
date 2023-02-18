<style lang="scss" scoped></style>
<template>
  <BaseViewer title="To-Do Viewer" itemType="todos" v-model:itemList="todoList">
    <template v-slot:hero>
      <img src="/todo.jpg" alt="Todo photo" />
      <p>
        Photo by
        <a
          href="https://unsplash.com/@eberhardgross?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
          >eberhard 🖐 grossgasteiger</a
        >
        on
        <a
          href="https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
          >Unsplash</a
        >
      </p>
    </template>
    <template v-slot:metrics>
      <div>
        {{ completedItems.length }} completed |
        {{ remainingItems.length }} remaining
      </div>
    </template>
  </BaseViewer>
</template>
<script setup>
import { ref, computed } from "vue";
import BaseViewer from "./BaseViewer.vue";

const todoList = ref([]);

const completedItems = computed(() => {
  return todoList.value.filter((item) => item.completed);
});

const remainingItems = computed(() => {
  return todoList.value.filter((item) => !item.completed);
});
</script>
