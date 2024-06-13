<template>
    <header class="navbar 
    navbar-expand-lg 
    navbar-light bg-light 
    justify-content-center 
    align-items-center">

        <h1>
            {{ mainHeader }}
              <!-- {{ title }} -->
        </h1>
    </header>
    
</template>
<script>
export default {
    // props:{
    //     title: String,
    // }
    data() {
        return {
            mainHeader: 'Learning Hup'
        }
    },
}
</script>

<style scoped>
header {
  /* width: 100%; */
  height: 5rem;
  /* background-color: #640032; */
  display: flex;
  /* justify-content: center; */
  /* align-items: center; */
}

header h1 {
  color: rgb(39, 38, 39);
  margin: 0;
}
</style>