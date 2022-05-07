<template>
    <div>
        <ul>
            <li v-for="job in jobs" :key="job.id">
                <h2>{{ job.title }} in {{ job.location }}</h2>
                <div>
                    <p><b>{{ job.salary }} euros</b></p>
                </div>
                <div>
                    <p>asdfasdf asdfasdfasdfa sdasdfasdfasdfa sdasdfasd</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
    import { defineComponent, PropType} from 'vue'
    import Job from "@/types/job";
    export default defineComponent({
        name: 'jobsList',
        props:  {
            jobs: {
                required: true,
                type: Array as PropType<Job[]>
            }
        }
    });
</script>

<style scoped>

</style>