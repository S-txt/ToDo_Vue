<template>
  <div class="todoListWrapper">
    <div v-for="todo of storeTodo.todos" :key="todo.id" class="card m-3 p-3 flex-row justify-content-between flex-gap-2">
      <div>
        <h5>{{ todo.title }}</h5>
        <div v-if="todo?.description">{{ todo?.description }}</div>
      </div>
      <button type="text" class="btn btn-danger" @click="storeTodo.removeTodo(todo.id)">Remove</button>
    </div>
  </div>
</template>

<script setup>
import { useTodoStore } from "../stores/todo";

const storeTodo = useTodoStore();
</script>

<style scoped>
.todoListWrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  flex-wrap: wrap;
}
.todoListWrapper > div {
  overflow: scroll;
}

.todoListWrapper button {
  margin-left: 16px;
}
</style>