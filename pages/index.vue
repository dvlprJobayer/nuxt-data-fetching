<script setup>
const users = await $fetch("https://jsonplaceholder.typicode.com/users");

const { data: users2 } = await useFetch(
  "https://jsonplaceholder.typicode.com/users"
);

const { pending, data: users3 } = await useLazyFetch(
  "https://jsonplaceholder.typicode.com/users"
);
</script>

<template>
  <NuxtLink to="/about">About</NuxtLink>
  <h1>Users</h1>
  <p v-if="pending">Loading ...</p>
  <ul v-else>
    <li v-for="user in users2" :key="user.id">{{ user.name }}</li>
  </ul>

  <ul>
    <li v-for="user in users" :key="user.id">{{ user.name }}</li>
  </ul>

  <ul>
    <li v-for="user in users2" :key="user.id">{{ user.name }}</li>
  </ul>
</template>
