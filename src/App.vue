<!--<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>-->

<template>
  <div id="app">
    <HelloWorld></HelloWorld>
    <!-- <selfBilling></selfBilling> -->
    <router-view/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import selfBilling from './views/Home.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    selfBilling,
  },
  data() {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
