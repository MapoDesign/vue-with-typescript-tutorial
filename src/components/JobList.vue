<script lang="ts">
import { defineComponent, PropType } from "vue";
import Job from "@/types/Jobs";

export default defineComponent({
  props: {
    jobs: {
      type: Array as PropType<Job[]>,
      required: true,
    },
  },
});
</script>

<template>
  <div class="job-list">
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
