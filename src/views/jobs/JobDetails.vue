<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>The Job id is {{ id }}</p>
    <p>{{job.details}}</p>
  </div>
  <div v-else>
    <p>Loading job details ... </p>
  </div>
  <!-- <p>The Job id is {{ $route.params.id }}</p> -->
</template>

<script>
export default {
    props: ['id'],
    data () {
      return {
        job: null
      }
    },
    // data () {
      mounted () {
        fetch('http://localhost:3000/jobs/' + this.id)
            .then((res) => res.json())
            .then(data => this.job = data)
            .catch(err => console.log(err.message)) 
      }
    //         id: this.$route.params.id
    //     }
    // }
    
}
</script>

<style>

</style>