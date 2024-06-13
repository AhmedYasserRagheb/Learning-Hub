<template>
  <base-alert v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>Unfortunately, at least one input value is invalid.</p>
      <p>Please check all inputs and make sure you enter at least a few characters into each input field.</p>
    </template>
    <template #actions>
      <button @click="confirmError" class="btn btn-dark">Okay</button>
    </template>
  </base-alert>
  <!-- <base-card> --> 
  <form @submit.prevent="saveData">
    <div class="form-control">
      <label for="title">Title</label>
      <input id="title" name="title" type="text" ref="resourceTitle" />
    </div>
    <div class="form-control">
      <label for="description">Description</label>
      <textarea id="description" name="description" rows="3" ref="resourceDescription"></textarea>
    </div>
    <div class="form-control">
      <label for="link">Link</label>
      <!-- <input id="link" name="link" type="url"/> -->
      <input type="url" name="link" id="link" ref="resourceUrl">
    </div>
    <div>
      <button type="submit" class="btn btn-secondary secondary">
        Add Resource
      </button>
    </div>
  </form>
  <!-- </base-card> -->
</template>

<script>
import BaseAlert from '../ui/BaseAlert.vue'
export default {
  components:{
    BaseAlert,
  },
  inject: ['userInput'],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    saveData() {
      const resourceTitle = this.$refs.resourceTitle.value;
      const resourceDesc = this.$refs.resourceDescription.value;
      const resourceUrl = this.$refs.resourceUrl.value;

      if (
        resourceTitle.trim() === '' ||
        resourceDesc.trim() === '' ||
        resourceUrl.trim() === ''
      ) {
        this.inputIsInvalid = true;
        return;
      }

      this.userInput(resourceTitle, resourceDesc, resourceUrl);
    },

    confirmError() {
      this.inputIsInvalid = false;
    }

  }
}
</script>

<style scoped>
form {
  width: 500px;
  margin: 20px auto;
}

label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}

.secondary {
  /* float:right */
  width: 100%;
}
</style>