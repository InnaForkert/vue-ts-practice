<template>
 <div class="app">
  <button @click="handleClick('title')">order by title</button>
  <button @click="handleClick('salary')">order by salary</button>
  <button @click="handleClick('location')">order by location</button>
  <JobList :jobs="jobs" :order="order" />
 </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import Job from "./types/Job";
import JobList from "./components/JobList.vue";
import OrderTerm from "./types/OrderTerm";

const jobs = ref<Job[]>([
 { title: "farm worker", location: "farm", salary: 20, id: "1" },
 { title: "killer", location: "killing station", salary: 200, id: "2" },
 { title: "suicide preventer", location: "MC Donalds", salary: 120, id: "3" },
 { title: "bottle opener", location: "KFC", salary: 2000, id: "4" },
 { title: "shit talker", location: "news", salary: 600, id: "5" },
]);

const order = ref<OrderTerm>("title");

const handleClick = (term: OrderTerm) => {
 order.value = term;
};
</script>

<style></style>
