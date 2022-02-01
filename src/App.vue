<template>
  <div id="app">
    <nav-bar/>
    <router-view/>
  </div>
</template>

<script>
import NavBar from './components/Navbar.vue'
import WelcomePage from './components/WelcomePage.vue'
import WindowsList from './components/WindowsList.vue'
import WindowDetails from './components/WindowDetails.vue'

export default {
  name: 'App',
  components: {
    WelcomePage,
    WindowsList,
    NavBar,
    WindowDetails
  }
}
</script>

<style>

</style>
