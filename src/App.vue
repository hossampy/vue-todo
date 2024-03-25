<template>
  
    <Navbar />
    <router-view/>
</template>

<script>
import Navbar from './components/Navbar.vue'
export default {
   
  components: {Navbar}
}

</script>

<style>
body {
background: rgb(237, 86, 255);
  background: linear-gradient(90deg, rgba(237, 86, 255, 1) 0%, rgba(75, 212, 255, 1) 100%);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: #000000;
}
</style>
