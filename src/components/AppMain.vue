<script>
import ArchetypeSelection from './ArchetypeSelection.vue';
import CardCollection from './CardCollection.vue';

import { state } from '../state.js';


export default {
    name: 'AppMain',
    emit: ['searchByArchetype'],
    components: {
        ArchetypeSelection,
        CardCollection
        
    },
    data() {
        return {
            state
        }
    },
    methods: {
        searchArchetype() {
            const urlByArchetype = this.state.url + `&archetype=${this.state.archetypeName}`
            this.state.fetchDataCard(urlByArchetype)
            console.log(this.state.archetypeName, urlByArchetype);
        }
    },
    created() {

        state.fetchDataCard(this.state.url);
        state.fetchDataArchetypes(this.state.urlArchetypesList)
    }
}
</script>

<template>
    <main>
        <div class="container">

            <ArchetypeSelection @search-by-archetype="searchArchetype" />
            <CardCollection />

        </div>
    </main>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;

main {
    background-color: $Yu_primary;
}
</style>

