<script lang="ts">
import { defineComponent, PropType } from "vue";
import Job from "@/types/Jobs";
import OrderTerms from "@/types/OrderTerms";

export default defineComponent({
  props: {
    jobs: {
      type: Array as PropType<Job[]>,
      required: true,
    },
    order: {
      type: String as PropType<OrderTerms>,
      required: true,
    },
  },
});
</script>

<template>
  <div class="job-list">
    <div class="job-list">
      <p>Order by {{ order }}</p>
    </div>
    <ul>
      <li v-for="job in jobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} euros</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Odit
            architecto hic laboriosam quibusdam similique nesciunt dolor. A
            aliquid expedita libero saepe cum, at, pariatur eaque quos
            architecto possimus, maiores assumenda.
          </p>
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
