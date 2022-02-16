<template>
  <div class="container">
    <!-- header template -->
    <Header />

    <!-- sidebar navigation template -->
    <Sidenav />
  </div>

  <router-view/>
</template>

<script>
import Header from './components/Header.vue'
import Sidenav from './components/Sidenav.vue'

export default {
  components: {
      Header,
      Sidenav
  }
}
</script>

<style src="./assets/css/style.css" lang="css" />