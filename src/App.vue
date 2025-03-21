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
/* Global scrollbar color */
:root {
  --scrollbar-color: #a98c7a;
  --scrollbar-thumb-color: #97796a;
}

/* Firefox */
* {
  scrollbar-width: thin;
  scrollbar-color: var(--scrollbar-thumb-color) var(--scrollbar-color);
}

/* Chrome, Edge, and Safari */
*::-webkit-scrollbar {
  width: 12px;
  background-color: var(--scrollbar-color);
}

*::-webkit-scrollbar-track {
  background: var(--scrollbar-color);
}

*::-webkit-scrollbar-thumb {
  background-color: var(--scrollbar-thumb-color);
  border-radius: 20px;
  border: 3px solid var(--scrollbar-color);
}

/* Mobile WebKit */
@media (max-width: 768px) {
  body {
    -webkit-overflow-scrolling: touch;
  }
  
  ::-webkit-scrollbar {
    width: 3px !important;
  }
  
  /* For iOS momentum scrolling */
  .v-main {
    -webkit-overflow-scrolling: touch;
    overflow-y: scroll;
  }
}

/* For mobile browsers that support color-scheme */
@media (max-width: 768px) {
  :root {
    color-scheme: light;
  }
  
  body {
    background-color: var(--scrollbar-color) !important;
  }
}
</style>
