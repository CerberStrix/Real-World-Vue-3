<script setup>
import EventService from '@/services/EventService.js'
import EventCard from "../components/EventCard.vue";
import { onMounted, ref } from 'vue'

const events = ref(null)

onMounted(() => {
  EventService.getEvents()
    .then((response) => events.value = response.data)
})
</script>

<template>
  <div class="home">
    <h1>Events For Good</h1>
    <div class="events">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
    </div>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>