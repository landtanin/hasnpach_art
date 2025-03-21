<template>
  <v-container fluid class="pa-0 ma-0" :class="{ 'fill-height': !isMobile }">
    <v-row no-gutters :class="{ 'fill-height': !isMobile }" justify="center">
      <v-col cols="12" class="image-container">
        <v-card flat class="image-wrapper" :class="{ 'mobile': isMobile, 'mobile-landscape': isMobileDevice && isLandscape }">
          <v-img
            :src="artImage"
            position="top"
            :height="isMobile ? 'auto' : '100vh'"
            :cover="!isMobile || (isMobileDevice && isLandscape)"
            :contain="isMobile && !isLandscape"
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
import artImageDesktop from '../assets/Hanspach-art_1920x1080.jpg'

// Standard breakpoint
const MOBILE_BREAKPOINT = 768

const windowWidth = ref(window.innerWidth)
const windowHeight = ref(window.innerHeight)

// Check if the device is in landscape orientation
const isLandscape = computed(() => {
  return windowWidth.value > windowHeight.value
})

// Check if we're on a mobile device
const isMobileDevice = computed(() => {
  return windowWidth.value <= MOBILE_BREAKPOINT
})

// We're in mobile mode if we're on a mobile device AND in portrait orientation
const isMobile = computed(() => {
  return isMobileDevice.value && !isLandscape.value
})

const getResponsiveImage = computed(() => {
  // If it's a mobile device in landscape, use desktop image
  if (isMobileDevice.value && isLandscape.value) {
    return artImageDesktop
  }
  // Otherwise follow the normal responsive rules
  if (isMobileDevice.value) {
    return artImageMobile
  }
  return artImageDesktop
})

const handleResize = () => {
  windowWidth.value = window.innerWidth
  windowHeight.value = window.innerHeight
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

.image-wrapper.mobile-landscape {
  height: 100vh;
  overflow: hidden;
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
