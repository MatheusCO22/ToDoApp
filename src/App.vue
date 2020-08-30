<template>
  <v-app>
    <router-view/>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {

  },
  data () {
    return {
      
    }
  }
}
</script>

<style>
  .rounded{
    border-radius: 15px;
  }
  .debug{
    border: 1px solid red;
  }
</style>
