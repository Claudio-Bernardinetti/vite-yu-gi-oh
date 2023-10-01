<script>
    import Card from './Card.vue';
    import Loader from './Loader.vue';
    import CardCounter from './CardCounter.vue';
    import { state } from '../state.js';
    
    
    export default {
        name: 'CardCollection',
    
        data() {
            return {
                state
            };
        },
        created() {
            state.fetchDataCard(this.state.url);
        },
        components: {
            Card,
            Loader,
            CardCounter
        }
    }
    </script>

<template>
    <div class="card_list">

        <CardCounter />

        <loader v-if="!state.status"></loader>
        <div v-else
            class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5 g-3">
            <card :card="card" v-for="(card, index) in state.cards" :key="index"></card>
        </div>

    </div>
</template>

<style lang="scss">


    
    .card_list {
        background-color: white;
        padding: 3rem;
    
        .found {
            background-color: black;
            color: white;
            padding: 1rem;
        }
    }
</style>