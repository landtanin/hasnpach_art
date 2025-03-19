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
    
    <!-- Email Subscription Box -->
    <div class="subscription-container">
      <v-sheet 
        width="450" 
        class="subscription-box mx-auto pa-4 rounded-lg"
        elevation="4"
      >
        <h3 class="text-h6 font-weight-medium mb-2">Subscribe to Our Newsletter</h3>
        <p class="text-body-2 mb-4">Stay updated with our latest art collections and exhibitions</p>
        <v-form @submit.prevent="submitSubscription">
          <v-row>
            <v-col cols="8">
              <v-text-field
                v-model="email"
                label="Your Email"
                variant="outlined"
                density="compact"
                hide-details
                placeholder="email@example.com"
                type="email"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="4">
              <v-btn 
                class="dark-button" 
                block
                height="40"
                type="submit"
              >
                Subscribe
              </v-btn>
            </v-col>
          </v-row>
        </v-form>
      </v-sheet>
    </div>
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
