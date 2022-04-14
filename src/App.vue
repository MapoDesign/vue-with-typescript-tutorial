<template>
  <div class="app">
    <p>{{ jobs[0].location }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "./types/Jobs";

export default defineComponent({
  name: "App",
  components: {},
  setup() {
    const jobs = ref<Job[]>([
      { title: "frontend developer", location: "Milan", salary: 30000, id: 1 },
      { title: "backend developer", location: "London", salary: 40000, id: 2 },
      { title: "fullstack developer", location: "Paris", salary: 35000, id: 3 },
      { title: "frontend developer", location: "Berlin", salary: 21000, id: 4 },
      {
        title: "fullstack developer",
        location: "Madrid",
        salary: 32000,
        id: 5,
      },
    ]);
    return {
      jobs,
    };
  },
});
</script>

<style></style>
