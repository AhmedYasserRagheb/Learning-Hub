<template>
  <li>
    <div>
    <header>
      <h3>{{ resourceTitle }}</h3>
      <base-button mode="flat" @click="removeResource(id)">Delete</base-button>
    </header>
    <p>{{ resourceDescription }}</p>
    <nav>
      <a :href="resourceUrl">View Resource</a>
    </nav>
  </div>
  </li>
</template>

<script>
import BaseButton from '../ui/BaseButton.vue';

export default {
  props:["id", "resourceTitle", "resourceDescription", "resourceUrl"],
  inject:["removeResource"],

  components:{
    BaseButton,
  }
}
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>