<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
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

  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });

    return {
      orderedJobs,
    };
  },
});
</script>

<template>
  <div class="job-list">
    <div class="job-list">
      <p>Order by {{ order }}</p>
    </div>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <img src="../assets/rupee.svg" alt="value" />
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
      </li></transition-group
    >
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
.list-move {
  transition: all 1s ease-in-out;
}
</style>
