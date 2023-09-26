<script>
import { state } from "../state.js";

export default {
  name: 'AppMain',
  data() {
    return {
      state
    }
  },
  created() {
    state.fetchData()
  }
}
</script>
<template>
  <main class="">

    <section class="characters container_cl" v-if="state.characters">

      <div class="container ">

        <div class="row row-cols-1 row-cols-sm-3 g-3">

          <div class="col-sm-12 col-md-6 col-lg-4 col-xl-3" v-for="character in state.characters" :key="character.id">

            <div class="card">
              <img :src='character.card_images[0].image_url' alt='' />

              <div class="card-body justify-content-center mb-5">
                <h4>{{ character.name }}</h4>
                <div class="meta">
                   {{ character.archetype }}
                </div>  
              </div>

            </div>

          </div>
          
        </div>
      </div>
    </section>
    <div class="loader text-center" v-else>
      <strong role="status">Caricamento
                    delle mail in
                    corso, attendere...
        </strong>
        <div class="spinner-grow  p-1 text-success"
                    aria-hidden="true">
        </div>
            
    </div>


  </main>
</template>

<style lang="scss" scoped >
@use '../assets/scss/partials/variables' as *;

  .container_cl {
    background-color: $Yu_primary;
  }
</style>