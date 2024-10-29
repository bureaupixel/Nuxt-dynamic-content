<template>
    <div class="montserrat-bold mt-10 mb-2">
      {{ sitetitle }}
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  import Data from './assets/data/settings.json';

  const SettingsData = ref(Data);
  
  // Computed property for sitetitle
  const sitetitle = computed(() => SettingsData.value.sitetitle);
  console.log(sitetitle)
  </script>
  