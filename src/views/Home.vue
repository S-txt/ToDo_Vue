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
          <aside>
            <Form/>
          </aside>

          <section>
            <List/>
          </section>
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
  flex-flow: row;

}
section > div {
  display: flex;
  flex-flow: column;
}
</style>