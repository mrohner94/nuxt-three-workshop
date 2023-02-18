<style lang="scss" scoped>
@import "./node_modules/bulma/bulma.sass";
@import "./assets/styles/main.scss";
.heading {
  color: $textColor;
}
.todo-list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
<template>
  <div class="section">
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
    <h1 class="title">Hello Workshop</h1>
    <button @click="fetchTodoList">Fetch Data</button>
    <ul class="todo-list">
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
      </li>
    </ul>
  </div>
</template>
<script setup>
import { ref } from "vue";

const todoList = ref([]);

const fetchTodoList = () => {
  fetch("https://jsonplaceholder.typicode.com/todos/").then((response) => {
    response.json().then((res) => {
      todoList.value = res;
    });
  });
};
</script>
