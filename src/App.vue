<template>
  <main-header></main-header>
  <the-resources></the-resources>
</template>

<script>
import MainHeader from './components/layout/MainHeader.vue';
import TheResources from './components/resources/TheResources.vue';

export default {
  components:{
   MainHeader,
   TheResources,
  },
  
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
