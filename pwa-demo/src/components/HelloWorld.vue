<script setup>
import { ref } from 'vue'

const hasPermission = ref(Notification.permission)

async function requestPermission() {
  const result = await Notification.requestPermission()
  hasPermission.value = result
}

async function sendNotification() {
  if (Notification.permission !== 'granted') {
    const result = await Notification.requestPermission()
    hasPermission.value = result
    if (result !== 'granted') return
  }
  const registration = await navigator.serviceWorker.getRegistration()
  if (registration) {
    registration.showNotification('Hello from PWA demo', {
      body: 'This is a test notification.',
      icon: '/icons/icon-192x192.png'
    })
  } else {
    new Notification('Hello from PWA demo', { body: 'This is a test notification.' })
  }
}
</script>

<template>
  <h1>PWA Notification Demo</h1>
  <p>Notification permission: {{ hasPermission }}</p>
  <button @click="requestPermission">Request Permission</button>
  <button @click="sendNotification">Send Notification</button>
</template>

<style scoped>
button {
  margin-right: 0.5rem;
}
</style>
