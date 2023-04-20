<template>
  <div class="container">

    <headerComponent />
  
    <main>

      <characterList/>
    </main>
    
  </div>
</template>

<script>
import { store } from './data/store';
import axios from 'axios';
import headerComponent from './components/headerComponent.vue';
import characterList from './components/characterCard.vue';


export default {
  name: 'App',
  components: {
    headerComponent,
    characterList
    
},
data(){
  return{
    store
  }
},
methods: {
  getCharacters(){
    const url = store.baseUrl + store.endpoint;
    axios.get(url).then((res) => {
      this.store.characterList = res.data.results;
    });
  }
},
mounted() {
  store.endpoint = 'character';
  this.getCharacter();
}
}
</script>

<style lang="scss" scoped></style>