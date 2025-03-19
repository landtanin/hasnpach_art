<template>
  <v-container fluid class="pa-0 ma-0 fill-height">
    <v-row no-gutters class="fill-height">
      <v-col cols="12">
        <v-card flat>
          <v-img
            src="@/assets/elke-art.jpg"
            height="100vh"
            width="100%"
            cover
            alt="Hasnpach Art"
          >
          </v-img>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts" setup>
  import { ref } from 'vue'
  
  const email = ref('')
  
  const submitSubscription = () => {
    // Here you would implement the actual subscription logic
    // For example, sending the email to your backend API
    console.log('Subscription request for:', email.value)
    // Reset the form
    email.value = ''
    // You could also add a success notification here
  }
</script>

<style scoped>
.v-container {
  max-width: 100%;
  position: relative;
}

.subscription-container {
  position: fixed;
  bottom: 16px; /* Approximately 1-2cm from bottom edge */
  left: 0;
  right: 0;
  z-index: 100;
  padding: 0 16px;
}

.subscription-box {
  background-color: rgba(193, 171, 161, 0.2);
  backdrop-filter: blur(10px);
}

.dark-button {
  background-color: #12110F !important;
  color: white !important;
}
</style>
