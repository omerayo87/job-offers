<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <jobsList :jobs="jobs" :order="order"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref} from 'vue';
import Job from "@/types/job";
import OrderTerm from "@/types/orderTerm";
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
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, handleClick, order }
  }
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
    color: white;
    border: 2px solid white;
    border-radius: 4px;
    background: #05B9E7;
    padding: 8px 16px;
    cursor: pointer;
    font-weight: bold;
  }

</style>
