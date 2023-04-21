<script>
import { store } from '../data/store';
    export default {
        name: 'characterList',
        components:{

        },
        data(){
            return{
                store
            }
        }
    }
</script>

<style lang="scss">

</style>

<template>
    <div class="container">
        <div class="row">
            <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="(character, index) in store.characterList" :key="character.id">
                {{ character.name }}
            </div>
        </div>
    </div>
</template>