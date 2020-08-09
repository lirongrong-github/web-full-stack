<template>
  <div id="app">

    <FormTest></FormTest>

  </div>
</template>

<script>

  import FormTest from '@/components/Form/index'

  export default {
  
    name: 'App',
    components: {

      FormTest

    }

  }

</script>

<style lang="scss">

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

</style>
