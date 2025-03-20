<template>
  <v-app :style="{ 'background-color': '#a98c7a' }">
    <router-view />
  </v-app>
</template>

<script lang="ts" setup>
  import { onMounted } from 'vue'
  
  onMounted(() => {
    console.log('App mounted successfully')
    console.log('Base URL:', import.meta.env.BASE_URL)
    console.log('Mode:', import.meta.env.MODE)
  })
</script>

<style>
/* Firefox */
* {
  scrollbar-width: thin;
  scrollbar-color: #a98c7a #a98c7a;
}

/* Chrome, Edge, and Safari */
*::-webkit-scrollbar {
  width: 12px;
}

*::-webkit-scrollbar-track {
  background: #a98c7a;
}

*::-webkit-scrollbar-thumb {
  background-color: #97796a;
  border-radius: 20px;
  border: 3px solid #a98c7a;
}
</style>
