<template>
  <div class="container">

    <headerComponent />

    <main>
      <div class="row">
        <div v-for="card in store.characterList" class="col-12 col-sm-6 col-md-4 col-lg-3 text-center card">
          <img :src="card.card_image" :alt="card.name">
           <div>{{ card.name }}</div>
           <div>{{ card.race }}</div>
        </div>
      </div>
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
  data() {
    return {
      store
    }
  },
  methods: {
    getCharacters() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0').then((res) => {
        console.log(res.data.data)
        store.characterList = res.data.data;
      });
    }
  },
  mounted() {
    this.getCharacters();
  }
}
</script>

<style lang="scss" scoped>
  .card{
    background-color: orange;
  }
</style>