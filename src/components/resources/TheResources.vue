<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode">
      Stored Resources
    </base-button>

    <base-button @click="setSelectedTab('add-resources')" :mode="addResButtonMode">
      Add Resource
    </base-button>
  </base-card>

  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import BaseCard from '../ui/BaseCard.vue';
import BaseButton from '../ui/BaseButton.vue';
import StoredResources from './StoredResources.vue';
import AddResources from './AddResources.vue';

export default {
  components: {
    BaseCard,
    BaseButton,
    StoredResources,
    AddResources,
  },

  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        // {
        //   id: 1,
        //   title: " title-1 ",
        //   desc: " desc for title 1",
        //   link: " https://google.org",
        // },
        // {
        //   id: 2,
        //   title: " title-2 ",
        //   desc: " desc for title 2",
        //   link: " https://google.org",
        // },
      ]
    }
  },
  provide() {
    return {
      resources: this.storedResources,
      userInput: this.addResource,
      removeResource: this.delete,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resources' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    delete(id){
      const resIndex = this.storedResources.findIndex(item => item.id === id);
      this.storedResources.splice(resIndex, 1);
    }
  },
}
</script>