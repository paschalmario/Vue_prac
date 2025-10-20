<script setup>
import Hero from '@/components/Hero.vue'
import HomeCards from '@/components/HomeCards.vue'
import JobListings from '@/components/JobListings.vue'
</script>
<template>
  <Hero />
  <HomeCards />
  <JobListings :Limit="4" :ShowButton="true" />
</template>
