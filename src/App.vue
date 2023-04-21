<template>
  <div class="container">

    <headerComponent />
  
    <main>

      <characterList/>
      
    </main>
    
  </div>
</template>

<script>
import axios from 'axios';
import { store } from './data/store';
import headerComponent from './components/headerComponent.vue';
import characterList from './components/characterCard.vue';
import characterCard from './components/characterCard.vue';


export default {
  name: 'App',
  components: {
    headerComponent,
    characterList,
    characterCard
    
},
data(){
  return{
    store
  }
},
methods: {
  getCharacters(){
    axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0').then((res) =>{
      console.log(res.data.name)
      store.characterList = res.data.name;
    });
  }
},
mounted() {
  this.getCharacters();
}
}
</script>

<style lang="scss" scoped></style>