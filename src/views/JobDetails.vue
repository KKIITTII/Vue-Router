<<template>
    <div v-if="job !== null">
        <h1>Job Details Page</h1>
        <h2>{{job.title}}</h2>
        <p>The job is {{id}}</p>
        <h2>{{job.details}}</h2>
    </div>   
    <div v-else>
        Loading
        Loading
        Loading
        Loading
        Loading
        Loading
    </div> 
</template>



<script setup>
// import {ref} from 'vue';

// const id = ref(this.$route.params.id)
import {defineProps, onMounted, reactive, ref} from 'vue';
const props = defineProps(['id'])

const job = ref(null)
const isLoading = ref(false)

onMounted(async () => {
  isLoading.value = true;
  try {
    const response = await fetch('http://localhost:3000/jobs/' + props.id);
   
    if (!response.ok) {
      throw new Error(`Failed to fetch jobs: ${response.statusText}`);
    }
    const data = await response.json();
    console.log("data:  ", data)
    job.value = data;
  } catch (err) {
   console.log( err.message);
  } finally {
    isLoading.value = false;
  }
});

// defineProps({
//     id
// })
</script>
