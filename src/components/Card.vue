<script>
import { state } from '../state.js';

export default {
    name: 'AppCard',
    props: {
        card: Object
    },
    data() {
        return {
            state
        };
    }
}
</script>

<template>
    <div class="col">

        <div class="card rounded-0 border-0">

            <img :src="card.card_images[0].image_url" class="card-img-top" alt="...">

            <div class="card-body">

                <div class="card-text d-flex flex-column justify-content-between h-100">

                    <div class="name">
                        {{ card.name }}
                    </div>

                    <div class="archetype">
                        {{ card.archetype }}
                    </div>

                </div>


            </div>

        </div>

    </div>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;

.card-body {
    background-color: $Yu_primary;
    height: 125px;
    border: 1px solid black;

    .name {
        color: white;
        text-transform: uppercase;
        font-weight: bold;
        font-size: 0.8rem;
        text-align: center;

    }

    .archetype {
        text-align: center;
    }
}
</style>