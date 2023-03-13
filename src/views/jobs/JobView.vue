<template>
    <h1>Jobs</h1>
    <h2 v-if="jobs.length < 1">Loading...</h2>
    <div class="job" v-for="job in jobs" :key="job.id">
        <router-link :to="{name: 'JobDetails', params: { id: job.id }}">
            <h2>{{ job.title }}</h2>
        </router-link>
    </div>
</template>

<script>
export default {
    data() {
        return {
            jobs: []
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs')
            .then(res => res.json())
            .then(data => this.jobs = data)
            .catch(err => console.log(err.message))
    }
}

</script>

<style>
    .job h2 {
        background: #F4F4F4;
        padding: 20px;
        border-radius: 10px;
        margin: 10px auto;
        max-width: 600px;
        cursor: pointer;
        color: #444;
    }

    .job h2:hover {
        background: #DDD;
    }

    .job a {
        text-decoration: dashed;
    }
</style>