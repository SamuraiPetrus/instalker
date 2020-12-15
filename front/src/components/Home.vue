<template>
    <div class="home container" v-show="!found">
        <div class="home-content pl-4 pr-4 is-flex is-flex-direction-column is-justify-content-center is-align-items-center">
            <img alt="Instalker logo" src="../assets/instalker-logo.png">
            <h1 class="is-size-1 mt-3">In<strong>Stalker</strong></h1>
            <VueTyper
            :text='["Stalk people on Instagram like a PRO.", "Who are you stalking today?", "Why are you stalking people anyway? Weirdo.", "What about stalking @natalieportman today?"]'
            :repeat='Infinity'
            :shuffle='false'
            initial-action='typing'
            :pre-type-delay='70'
            :type-delay='30'
            :pre-erase-delay='2000'
            :erase-delay='250'
            erase-style='select-all'
            :erase-on-complete='false'
            caret-animation='blink'>
            </VueTyper>
            <div class="mb-5"></div>
            <Searchform></Searchform>
        </div>
    </div>
</template>

<script>
    var VueTyper = window.VueTyper.VueTyper
    import Searchform from './Searchform.vue'
    export default {

        data () {
            return {
                found: false
            }
        },

        components: {
          VueTyper,
          Searchform
        },

        created () {
            Event.listen('userFound', () => { this.found = true })
        }
    }
</script>

<style>

  .home,
  .home-content{
    height: 100vh;
  }

  .home-content{
    margin-top: -40px;
  }

</style>
