<template>
<div>
    <nav class="mb-2">
        <ul>
            <li class="montserrat-bold pr-2 inline" v-for="data in ContentData" :key="ContentData.id">
                <NuxtLink :to="`/page${data.id}`">
                    {{ data.title }}
                </NuxtLink>
            </li>
        </ul>
    </nav>
</div>
</template>

<script setup>
import Data from './assets/data/data.json'
const ContentData = ref(Data);
</script>
