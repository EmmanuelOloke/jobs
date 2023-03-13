<template>
    <div v-if="job">
        <h1>{{job.title}}</h1>
        <p>The job id is: {{ job.id }}</p>
        <p>The job Detail is: {{ job.details }}</p>
    </div>
    <h1 v-else>Loading...</h1>
</template>

<script>
    export default {
        props: ['id'],
        data() {
            return {
                job: null
            }
        },
        mounted() {
            fetch(`http://localhost:3000/jobs/${this.id}`)
                .then(res => res.json())
                .then(data => this.job = data)
                .catch(err => console.log(err))
        }
    }
</script>

<style>

</style>