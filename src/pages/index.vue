<template>
  <v-container fluid class="pa-0 ma-0 fill-height">
    <v-row no-gutters class="fill-height">
      <v-col cols="12">
        <v-card flat class="image-wrapper">
          <v-img
            src="@/assets/haspnach-art.jpg"
            height="100vh"
            contain
            position="center"
            alt="Hasnpach Art"
            class="main-image"
          >
          </v-img>
        </v-card>
      </v-col>
    </v-row>
    
    <!-- Contact Button -->
    <div class="contact-button-container">
      <a 
        href="mailto:atelier@inkvalley-london.com" 
        class="contact-button"
        target="_blank"
        rel="noopener noreferrer"
      >
        CONTACT
      </a>
    </div>
  </v-container>
</template>

<style scoped>
.v-container {
  max-width: 100%;
  position: relative;
}

.image-wrapper {
  height: 100vh;
  background-color: transparent;
}

.main-image {
  height: 100%;
  width: 100%;
}

.contact-button-container {
  position: fixed;
  bottom: 60px;
  left: 0;
  right: 0;
  text-align: center;
  z-index: 100;
}

.contact-button {
  display: inline-block;
  font-size: 12px;
  letter-spacing: 3px;
  color: #F7A369;
  background-color: rgba(59, 44, 35, 0.4);
  text-decoration: none;
  padding: 8px 16px;
  border: 0.7px solid rgba(247, 163, 105, 0.7);
  font-weight: 500;
  text-transform: uppercase;
  transition: all 0.3s ease;
}

.contact-button:hover {
  background-color: rgba(59, 44, 35, 0.7);
  transform: scale(1.02);
}
</style>
