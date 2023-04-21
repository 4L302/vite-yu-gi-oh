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
            <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="card in store.characterlist">
                {{ card.name }}
            </div>
        </div>
    </div>
</template>