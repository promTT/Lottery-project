<template>
  <navbar/>
  <crud/>
</template>

<script>
import navbar from "./components/navbar.vue";
import crud from "./components/crud.vue"

export default {
  components: {
    'navbar': navbar,
    'crud': crud
    },
  name: 'App',
  data(){
    return{
      firstname: 'asdsd',
      d: 'dsadsad',
    }
  }
}
</script>

<style>
</style>
