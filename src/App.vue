<template>
  <v-app :style="{ 'background-color': '#AA8D78' }">
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
