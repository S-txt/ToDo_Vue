<template>
  <form @submit="onSubmit">

    <!-- title -->
    <div class="field">
      <label class="label">Title</label>
      <input type="text" class="input" name="title" v-model="title" />
    </div>

    <!-- description -->
    <div class="field">
      <label class="label">Description</label>
      <textarea class="input" name="description" v-model="description"></textarea>
    </div>

    <!-- submit -->
    <div class="field">
      <button type="submit">Create Todo</button>
    </div>
  </form>
</template>

<script>
import { defineComponent } from "vue";
import { useTodoStore } from "../stores/todo";

export default defineComponent({
  name: "TodoForm",
  data() {
    return {
      title: "",
      description: "",
    };
  },
  setup() {
    const storeTodo = useTodoStore();
    return { storeTodo };
  },
  methods: {
    onSubmit(Event) {
      Event.preventDefault();

      if (!this.title) {
        return;
      }

      // save data into store
      this.storeTodo.addTodo(this.title, this.description);

      // clear data
      this.title = "";
      this.description = "";
    },
  },
});
</script>

<style scoped>
.field {
  display: flex;
  flex-flow: column;
  padding: 12px;
  border-radius: 12px;
  background-color: #f8f9fa;
}

.label {
  font-size: 18px;
  font-weight: 600;
  color: #212529;
}

form {
  padding: 24px;
  background-color: #f8f9fa;
  border-radius: 8px;
  border: 1px solid;
}

button {
  padding: 8px;
  border-radius: 8px;
  color: #f8f9fa;
  background-color: #007BFF;
  cursor: pointer;
  font-weight: 600;
  font-size: 16px;
}

input {
  border-radius: 8px;
  height: 40px;
}

textarea {
  width: 100%;
  max-width: 100%;
  min-width: 100%;
  height: 126px;
}
</style>
