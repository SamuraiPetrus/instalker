<template>
    <header class="appheader">
        <div class="appheader-content is-flex is-flex-wrap-wrap is-align-items-center is-justify-content-space-between mb-5 pb-5 pt-5">
            <div class="appheader-brand is-flex is-align-items-center">
                <a href="javascript:void(0)" @click="backToHome()" class="appheader-back mr-4"><i class="fas fa-arrow-left"></i></a>
                <figure class="appheader-logo">
                    <img alt="Instalker logo" src="../assets/instalker-logo.png">
                </figure>
                <h2 class="ml-3 is-size-4">In<strong>Stalker</strong></h2>
            </div>
            <Searchform></Searchform>
        </div>
    </header>
</template>

<script>
    import Searchform from './Searchform.vue'
    export default {
      components: {
          Searchform
      },
      methods:{
          backToHome() {
              Event.fire('backToHome')
          }
      }
    }
</script>

<style>
    .appheader-content{
        border-bottom: 1px solid #c4c4c4;
    }
    .appheader-back{
        font-size: 25px;
    }
    .appheader-logo{
        height: 50px;
        width: 50px;
    }
    @media screen and ( max-width: 700px ) {
        .appheader-content{
            flex-direction: column;
            justify-content: center !important;
        }
        .appheader-brand{
            margin-bottom: 20px;
        }
    }
</style>
