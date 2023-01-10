<template>
  <div class="card m-3">
    <Form @submit="onSubmit" :validation-schema="schema">
      <div class="field">
        <label class="label">Title</label>
        <Field type="text" class="input form-control" name="title" />
      </div>
      <div class="field">
        <label class="label">Description</label>
        <Field class="input form-control" name="description" />
      </div>
      <div class="field">
        <button type="submit" class="btn btn-primary">Create Todo</button>
      </div>
    </Form>
  </div>
  
</template>

<script setup>
import * as Yup from 'yup';
import { Field, Form } from "vee-validate";
import { defineComponent } from "vue";
import { useTodoStore } from "../stores/todo";
import { useAlertStore } from "@/stores";

const schema = Yup.object().shape({
  title: Yup.string().required("Title is required"),
  description: Yup.string(),
})

function onSubmit(values, actions) {
    console.log()
    const storeTodo = useTodoStore();
    const alertStore = useAlertStore();
    try {
      storeTodo.addTodo(values.title, values.description);
      actions.setValues({title: "", description: ""});
    } catch (e) {
      alertStore.error(e);
    }
}
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
/* 
form {
  padding: 24px;
  background-color: #f8f9fa;
  border-radius: 8px;
  border: 1px solid;
} */

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
