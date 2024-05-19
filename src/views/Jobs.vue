<template>
   <div v-if="jobs.length !== 0">
        <div v-for="job in jobs" :key="job.id">
            <router-link :to="{ name: 'jobDetails', params: {id: job.id } }"> <h2> {{job.title}}</h2></router-link>
        </div>
   </div>
   <div v-else>
        Loading
        Loading
        Loading
        Loading
        Loading
        Loading
        Loading 
   </div>
</template>




<script setup>
import { ref, onMounted } from 'vue';

const jobs = ref([]);
const isLoading = ref(false);
const error = ref(null);

onMounted(async () => {
  isLoading.value = true;
  try {
    const response = await fetch('http://localhost:3000/jobs');
    if (!response.ok) {
      throw new Error(`Failed to fetch jobs: ${response.statusText}`);
    }
    const data = await response.json();
    jobs.value = data;
  } catch (err) {
    error.value = err.message;
  } finally {
    isLoading.value = false;
  }
});
</script>