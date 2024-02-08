<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavBar from './components/NavBar.vue'
import ImGSection from './components/IMGSection.vue'
import AboutUs from './components/AboutUs.vue'
import Footer from './components/Footer.vue'
import ReviewsSection from './components/ReviewsSection.vue'
import Services from './components/Services.vue'
import ReviewForm from './components/ReviewForm.vue'

</script>

<template>
  <NavBar />
  <ImGSection />
  <AboutUs />
  <Services></Services>
  <ReviewsSection></ReviewsSection>
  <ReviewForm></ReviewForm>
  <Footer></Footer>
  
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
