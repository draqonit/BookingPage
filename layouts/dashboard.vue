<template>
  <div>
    <div>
      <sidebar />
    </div>
    <div>
      <Nuxt />
    </div>
  </div>
    
</template>

<script>
import sidebar from '../components/userdetails/sidebar.vue'
export default {
  components: { sidebar },

}
</script>

<style>

</style>