<template>
    <v-container>
      <v-form ref="form" v-model="valid" @submit.prevent="submitForm">
        <v-text-field
          v-model="user.id"
          label="ID"
          :rules="[rules.required]"
        ></v-text-field>
        <v-text-field
          v-model="user.firstName"
          label="First Name"
          :rules="[rules.required]"
        ></v-text-field>
        <v-text-field
          v-model="user.lastName"
          label="Last Name"
          :rules="[rules.required]"
        ></v-text-field>
        <v-btn :disabled="!valid" color="primary" type="submit">Add User</v-btn>
      </v-form>
    </v-container>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue';
  
  const user = ref({
    id: '',
    firstName: '',
    lastName: ''
  });
  const valid = ref(false);
  const form = ref();
  
  const rules = {
    required: (value: string) => !!value || 'Required.'
  };
  
  const submitForm = async () => {
    try {
      const response = await fetch('https://6e3c4509-7a36-47b2-b8aa-af3e8d4f892b-00-275zxodyg5wnk.kirk.replit.dev/user', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(user.value)
      });
      if (response.ok) {
        alert('User added successfully!');
        user.value = { id: '', firstName: '', lastName: '' }; // Reset form
        form.value.reset();
      } else {
        alert('Failed to add user.');
      }
    } catch (error) {
      alert('Error: ' + error.message);
    }
  };
  </script>
  