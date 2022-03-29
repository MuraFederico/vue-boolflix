<template>
  <div id="app">
    <header-notflix />
    <main-notflix />
  </div>
</template>

<script>
import HeaderNotflix from './components/HeaderNotflix.vue'
import MainNotflix from './components/MainNotflix.vue'

export default {
  name: 'App',
  components: {
    HeaderNotflix,
    MainNotflix,
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>
