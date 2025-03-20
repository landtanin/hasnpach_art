<template>
  <v-container fluid class="pa-0 ma-0" :class="{ 'fill-height': !isMobile }">
    <v-row no-gutters :class="{ 'fill-height': !isMobile }" justify="center">
      <v-col cols="12" class="image-container">
        <v-card flat class="image-wrapper" :class="{ 'mobile': isMobile }">
          <v-img
            :src="artImage"
            position="top"
            :height="isMobile ? 'auto' : '100vh'"
            :cover="!isMobile"
            :contain="isMobile"
            alt="Hanspach Art"
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

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'
import artImageMobile from '../assets/Hanspach-art_mobile 430.jpg'
import artImageTablet from '../assets/Hanspach-art_1280x832.jpg'
import artImageDesktop from '../assets/Hanspach-art_1920x1080.jpg'

const windowWidth = ref(window.innerWidth)

const getResponsiveImage = computed(() => {
  if (windowWidth.value <= 430) {
    return artImageMobile
  } else if (windowWidth.value <= 1280) {
    return artImageTablet
  }
  return artImageDesktop
})

const isMobile = computed(() => {
  return windowWidth.value <= 430
})

const handleResize = () => {
  windowWidth.value = window.innerWidth
}

onMounted(() => {
  window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})

const artImage = computed(() => getResponsiveImage.value)
</script>

<style scoped>
.v-container {
  max-width: 100%;
  position: relative;
}

.image-container {
  margin: 0 auto;
}

.image-wrapper {
  height: 100vh;
  background-color: transparent;
}

.image-wrapper.mobile {
  height: auto;
}

.main-image {
  width: 100%;
}

.main-image:deep(.v-img__img) {
  object-position: top center;
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
  color: #ffa96d;
  background-color: transparent;
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
