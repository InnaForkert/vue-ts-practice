<script lang="ts" setup>
import { computed } from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

const props = defineProps<{
 jobs: Job[];
 order: OrderTerm;
}>();

const orderedJobs = computed(() => {
 return [...props.jobs].sort((a: Job, b: Job) =>
  a[props.order] > b[props.order] ? 1 : -1
 );
});
</script>

<template>
 <div class="job-list">
  <p>Ordered by {{ order }}</p>
  <ul>
   <li v-for="job in orderedJobs" :key="job.id">
    <h2>{{ job.title }} in {{ job.location }}</h2>
    <div class="salary">
     <p>{{ job.salary }} UAH</p>
    </div>
    <div class="description">
     Lorem ipsum dolor sit, amet consectetur adipisicing elit. Tempora eligendi,
     excepturi deserunt nostrum perferendis eaque ullam veritatis dolorem
     quaerat sit.
    </div>
   </li>
  </ul>
 </div>
</template>

<style scoped>
.job-list {
 max-width: 960px;
 margin: 40px auto;
}
.job-list ul {
 padding: 0;
}
.job-list li {
 list-style-type: none;
 background: white;
 padding: 16px;
 margin: 16px 0;
 border-radius: 4px;
}
.job-list h2 {
 margin: 0 0 10px;
 text-transform: capitalize;
}
.salary {
 display: flex;
}
.salary img {
 width: 30px;
}
.salary p {
 color: #17bf66;
 font-weight: bold;
 margin: 10px 4px;
}
</style>
