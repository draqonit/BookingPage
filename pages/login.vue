<template>
   <div class="flex w-screen h-screen">
     <topbar />

    <div>
      
       
       <loginpics />

    </div>

      <div class="bg-white w-full md:max-w-md lg:max-w-full md:mx-auto md:mx-0 md:w-1/2 xl:w-1/3 h-screen px-6 lg:px-16 xl:px-12
        flex items-center justify-center">

    
        <login />

      </div>


  </div>
</template>

<script>
import loginpics from '../components/loginpics.vue'
import Topbar from '../components/topbar.vue'
export default {
  components: { loginpics, Topbar },

}
</script>

<style>

</style>