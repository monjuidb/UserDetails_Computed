<script setup>
  import { ref,computed } from 'vue';  
  const user = ref({
    name: 'John Doe',
    birthdate: '1990-01-01',
    email: 'johndoe@example.com',
    description: 'A Vue.js enthusiast.',
    profileImage: 'https://example.com/profile.jpg'
  });

  const birthYear = computed(() => {
  const birthdate = new Date(user.value.birthdate);
  return birthdate.getFullYear();
    });
  const eligibilityMessage = computed(() => {
  const birthdate = new Date(user.value.birthdate);
  const age = new Date().getFullYear() - birthdate.getFullYear();

  if (age >= 18) {
    return 'You are eligible to vote.';
  } else {
    return 'You are not eligible to vote.';
  }
})
  </script>

<template>
    <div>
    <div>
        <label>Birth Year:</label>
        <span>{{ birthYear }}</span>
    </div>
    <div>
        <label>Eligibility to Vote:</label>
        <span>{{ eligibilityMessage }}</span>
    </div>
  </div>
  <div>
      <h1>User Details</h1>
      <div>
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="user.name" />
      </div>
      <div>
        <label for="birthdate">Birthdate:</label>
        <input type="date" id="birthdate" v-model="user.birthdate" />
      </div>
      <div>
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="user.email" />
      </div>
      <div>
        <label for="description">Description:</label>
        <textarea id="description" v-model="user.description"></textarea>
      </div>
      <div>
        <label for="profile-image">Profile Image URL:</label>
        <input type="url" id="profile-image" v-model="user.profileImage" />
        <img :src="user.profileImage" alt="Profile Image" />
      </div>
    </div>
  </template>
  
  
  