<template>
  <div> 

  <ul>
  	<router-link tag="li" to="./components/movie"></router-link>
  	<router-link tag="li" to="./components/cienma"></router-link>
  	<router-link tag="li" to="./components/personal"></router-link>

  </ul>
   <navbar></navbar>

   <router-view></router-view>
  </div>
  
</template>

<script>
import navbar from"./components/common/navbar"
import cinema from"./components/cinema"
export default {
  name: 'App'
}
</script>

<style>

</style>
