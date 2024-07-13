<script setup lang="ts">
import UserList from './components/UserList.vue';
import AddUser from './components/AddUser.vue';
import 'vuetify/styles';
</script>

<template>
  <v-app>
    <v-main>
      <v-container>
        <UserList />
        <AddUser />
      </v-container>
    </v-main>
  </v-app>
</template>
