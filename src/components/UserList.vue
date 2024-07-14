<script setup lang="ts">
import { onMounted, ref } from 'vue'

const userList = ref([]);

onMounted(async () => {
  const response = await fetch('https://6e3c4509-7a36-47b2-b8aa-af3e8d4f892b-00-275zxodyg5wnk.kirk.replit.dev/user');
  userList.value = await response.json();
});
</script>

<template>
  <p><strong>Users list</strong></p>
  <table>
    <thead>
    <tr><th>ID</th><th>First name</th><th>Last name</th></tr>
    </thead>
    <tbody>
    <tr v-for="(user, i) in userList" :key="i">
      <td>{{ user.id }}</td><td>{{ user.firstName }}</td><td>{{ user.lastName }}</td>
    </tr>
    </tbody>
  </table>
</template>

<style scoped>
table {
  border: 1px solid white;
  border-collapse: collapse;
}
table td, table th {
  border: 1px solid white;
  padding: 10px;
}
</style>