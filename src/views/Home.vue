<script setup>
import { storeToRefs } from 'pinia';

import { useAuthStore } from '@/stores';
import {Form, List} from "@/components";




const authStore = useAuthStore();
const { user } = storeToRefs(authStore);
</script>

<template>
    <div v-if="user">
        <h1>{{user.firstName}}'s to-do list</h1>
      <div class="todo">
          <Form />
          <List />
      </div>
    </div>
</template>
<style scoped>
section {
  width: 50%;
  margin-left: 10px;
}
.todo{
  display: flex;
  flex-direction: column;

}
section > div {
  display: flex;
  flex-flow: column;
}
</style>