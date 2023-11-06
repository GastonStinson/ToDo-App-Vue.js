<template>
  <div class="fondo">
    <NavBar />
    <ListaTareas />
  </div>
</template>

<script>
import ListaTareas from './components/ListaTareas'
import NavBar from './components/NavBar'

export default {
  name: 'App',
  components: {
    NavBar, 
    ListaTareas
  }
}
</script>

<style>
  .fondo {
    background-image: url("./assets/fondo.jpg");
    height: 100vh;
  }
</style>
