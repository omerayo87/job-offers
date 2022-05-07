<template>
  <div class="app">
    <jobsList :jobs="jobs"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref} from 'vue';
import Job from "@/types/job";
import jobsList from "@/components/jobsList.vue";

export default defineComponent({
  name: 'App',
  components: {
    jobsList
  },
  setup(){
    const jobs=ref<Job[]>([
      {
        id: '1',
        title: 'Frontend',
        location: 'Ciego de Avila',
        salary: 50000
      },
      {
        id: '2',
        title: 'Backend',
        location: 'Villa Clara',
        salary: 40000
      },
      {
        id: '3',
        title: 'Fullstack',
        location: 'Sancti Spiritus',
        salary: 40500
      },
      {
        id: '4',
        title: 'Devops',
        location: 'Granma',
        salary: 20000
      }
    ])
    return { jobs }
  }
});
</script>

<style>

</style>
