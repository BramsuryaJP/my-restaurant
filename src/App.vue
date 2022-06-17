<template>
  <NavbarComponent />
  <router-view/>
</template>
<script>
import NavbarComponent from './components/NavbarComponent.vue'
export default {
  name: "App",
  components: {
    NavbarComponent
  }
}
</script>
<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app{
  min-height: 100vh;
}

body {
  font-family: 'Poppins', sans-serif;
}
</style>
