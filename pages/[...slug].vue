<template>
    <div v-if="contentItem">
      <p 
        v-if="contentItem.title"
        class="montserrat-bold text-4xl">
        {{ contentItem.title }}
      </p>
      <p 
        v-if="contentItem.subtitle"
        class="montserrat-semibold text-xl">
        {{ contentItem.subtitle }}
      </p>
      <p 
        v-if="contentItem.description"
        class="opacity-50">
        {{ contentItem.description }}
      </p>
      <div
      v-if="contentItem.image"
      >
        <!-- Dynamically set the image from contentItem -->
        <NuxtImg :src="contentItem.image" fit="cover" />
      </div>
      <p 
        v-if="contentItem.body"
        >
        {{ contentItem.body }}
      </p>

      <p 
        v-if="contentItem.paragraph1"
        >
        {{ contentItem.paragraph1 }}
      </p>
      <p 
        v-if="contentItem.paragraph2"
        >
        {{ contentItem.paragraph2 }}
      </p>
      <p 
        v-if="contentItem.paragraph3"
        >
        {{ contentItem.paragraph3 }}
      </p>

    </div>
    <div v-else>
      <p>Content not found.</p>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  import { useRoute } from 'vue-router';
  import Data from './assets/data/data.json';
  
  const ContentData = ref(Data);
  const route = useRoute();
  
  // Create a ref containing the last part of the route path
  const lastPathSegment = ref(route.path.split('/page').pop());
  // console.log(lastPathSegment)
  // Find the object based on the last part of the route (assuming it’s the ID)
  const contentItem = computed(() => {
    return ContentData.value.find(item => item.id === parseInt(lastPathSegment.value));
  });
  </script>
  