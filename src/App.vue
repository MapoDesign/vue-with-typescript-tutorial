<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "./types/Jobs";
import OrderTerms from "./types/OrderTerms";
import JobList from "./components/JobList.vue";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: "fullstack developer", location: "Paris", salary: 35000, id: 3 },
      { title: "backend developer", location: "London", salary: 40000, id: 2 },
      { title: "frontend developer", location: "Berlin", salary: 21000, id: 4 },
      { title: "frontend developer", location: "Milan", salary: 30000, id: 1 },
      {
        title: "fullstack developer",
        location: "Madrid",
        salary: 32000,
        id: 5,
      },
    ]);

    const order = ref<OrderTerms>("title");

    const handleClick = (term: OrderTerms) => {
      order.value = term;
    };

    return {
      jobs,
      handleClick,
      order,
    };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
