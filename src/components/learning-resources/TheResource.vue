<template>
  <button @click="setSelectedTab('stored-resources')">Stores Resources</button>
  <button  @click="setSelectedTab('add-resource')" >Add Resources</button>

<keep-alive>
  <component :is="selectedTab"> </component>

</keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
  export default {
    components:{StoredResources, AddResource},
   data(){
    return {
      selectedTab : 'stored-resources',
      storedResources:[
      { id: "official-guide" , title:"official-guide",
      description:"the official vue.js documentatuin",
      link: 'https://vuejs.org'
      },

      { id: "google" , title:"google",
      description:"learn how to google",
      link: 'https://google.com'
      }
    ]
    }
   },

   provide(){
    return{
      resources: this.storedResources,
       addResource:this.addResource

    }
   },
   methods:{
    setSelectedTab(tab){
      this.selectedTab=tab
    },

    addResource(title, description,url){
        const newResource= {
          id: new Date().toISOString(),
          title:title,
          description:description,
          link:url

        };
        this.storedResources.unshift(newResource);
        this.selectedTab='stored-resources'
      }
   }
  }
</script>