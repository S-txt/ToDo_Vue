<template>
  <div>
    <div v-for="todo of storeTodo.todos" :key="todo.id" class="wrapper">
      <div class="header">
        <div class="title">{{ todo.title }}</div>
        <div>
          <button type="button" @click="storeTodo.removeTodo(todo.id)">remove</button>
        </div>
      </div>
      <div v-if="todo?.description">{{ todo?.description }}</div>
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { useTodoStore } from "../stores/todo";

export default defineComponent({
  name: "TodoList",
  setup() {
    const storeTodo = useTodoStore();

    return { storeTodo };
  },
});
</script>

<style>
.wrapper {
  padding: 24px;
  background-color: #f8f9fa;
  border-radius: 8px;
  border: 1px solid;
  margin-top: 16px;
}
.header {
  display: flex;
  justify-content: space-between;
}

.title {
  font-weight: 600;
  font-size: 18px;
}

button {
  padding: 8px;
  border-radius: 8px;
  color: #f8f9fa;
  background-color: #DC3545;
  cursor: pointer;
  font-weight: 600;
  font-size: 16px;
}
</style>
