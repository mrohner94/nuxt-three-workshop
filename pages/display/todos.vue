<style lang="scss" scoped>
@import "./node_modules/bulma/bulma.sass";
.todo-list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
<template>
  <NuxtLayout name="todo">
    <div class="section">
      <h1 class="title">Todo Viewer</h1>
      <NuxtPage v-if="route.params.id" />
      <BaseViewer v-else title="To-Do Viewer" v-model:itemList="todoList">
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
        <template v-slot:items>
          <ul class="todo-list">
            <li v-for="todo in displayedTodos" :key="`todo-id-${todo.id}`">
              <input type="checkbox" :checked="todo.completed" />
              <NuxtLink :to="`/display/todos/${todo.id}`">{{
                todo.title
              }}</NuxtLink>
            </li>
          </ul>
        </template>
      </BaseViewer>
    </div>
  </NuxtLayout>
</template>
<script setup>
import { ref, computed } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();
const todoList = ref([]);

const displayedTodos = computed(() => {
  if (route.query.completed == "true") {
    return completedItems.value;
  } else {
    return remainingItems.value;
  }
});

const completedItems = computed(() => {
  return todoList.value.filter((item) => item.completed);
});

const remainingItems = computed(() => {
  return todoList.value.filter((item) => !item.completed);
});
</script>
