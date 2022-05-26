<template>
    <div class="job-list">
        <samp>Order by: <b>{{ order }}</b></samp>
        <transition-group name="list" tag="ul">
            <li v-for="job in orderedJobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <div class="salary">
                    <img src="../assets/euro.png" alt="euro">
                    <p><b>{{ job.salary }}</b></p>
                </div>
                <div>
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
                        tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
                        quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
                        Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                        Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
                    </p>
                </div>
            </li>
        </transition-group>
    </div>
</template>

<script lang="ts">
    import { computed, defineComponent, PropType} from 'vue'
    import Job from "@/types/job";
    import OrderTerm from "@/types/orderTerm";
    export default defineComponent({
        name: 'jobsList',
        props:  {
            jobs: {
                required: true,
                type: Array as PropType<Job[]>
            },
            order: {
                required: true,
                type: String as PropType<OrderTerm>
            }
        },
        setup(props) {
          const orderedJobs = computed( () => {
                return [...props.jobs].sort((a: Job, b: Job) => {
                    return a[props.order] > b[props.order] ? 1 : -1
                })
          })
        return { orderedJobs }
        }
    });
</script>

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
        margin-top: 5px;
        width: 30px;
        height: 30px;
    }
    .salary p {
        color: #04C7F8;
        font-weight: bold;
        margin: 10px 4px;
    }
    .list-move {
        transition: all 1s;
    }
</style>